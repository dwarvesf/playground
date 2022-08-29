---
tags: engineering/mobile, ios, bluetooth, energy
author: Nguyen Tran Khanh
date: 2022-09-05
---

# Bluetooth LE IOS Swift
Given the proliferation of gadgets in today’s world, communication between those devices can lead to using those gadgets, and the information provided by those gadgets, in more effective ways. To this end, Apple has introduced the Core Bluetooth framework, which can communicate with many real-world devices such as heart rate sensors, digital thermostats, and workout equipment. If you can connect to it via BLE (Bluetooth Low Energy) wireless technology, the Core Bluetooth framework can connect to it.

Please note that the purpose here is not to implement a perfect nice best design pattern, but demonstrate how to use, at the best I can, the BLE on iPhone, iPad ( and soon on Mac )
it is better, for me, to provide a way for anybody to use my code, in the design pattern you could choose.
so : the code in iplemented in a simple design pattern. that's it :o)


## Centrals and Peripherals
A Bluetooth device can be either a central or peripheral:

* Central: the object that receives the data from a Bluetooth device.
* Peripheral: the Bluetooth device that publishes data to be consumed by other devices.
The iOS device will be the central, receiving data from the peripheral.


## Advertising Packets
Bluetooth peripherals broadcast some of the data they have in the form of advertising packets. These packets can contain information such as the peripheral’s name and main functionality. They can also include extra information related to what kind of data the peripheral can provide.

The job of the central is to scan for these advertising packets, identify any peripherals it finds relevant, and connect to individual devices for more information.




## Services and Characteristics
Advertising packets are very small and cannot contain a great deal of information. To share more data, a central needs to connect to a peripheral.

The peripheral’s data is organized into services and characteristics:

* Service: a collection of data and associated behaviors describing a specific function or feature of a peripheral. For example, a heart rate sensor has a Heart Rate service. A peripheral can have more than one service.
* Characteristic: provides further details about a peripheral’s service. For example, the Heart Rate service contains a Heart Rate Measurement characteristic that contains the beats per minute data. A service can have more than one characteristic. Another characteristic that the Heart Rate service may have is Body Sensor Location, which is simply a string that describes the intended body location of the sensor.
Each service and characteristic is represented by a UUID which can be either a 16-bit or a 128-bit value.


## What I do

The apps implement basic BLE communication:

* Central scans for Peripheral and connects to it
* Central reads a value from Peripheral
* Central writes a value to Peripheral
* Peripheral notifies Central that a value has changed

Each BLE Central is compatible with each BLE Peripheral, because they use the same service and characteristics UUIDs.

### Development tools

* Xcode - for iOS project

## Supported devices

Platform | Peripheral | Central | Notes
----- | ----- | ----- | -----
iOS | YES | YES | iOS 11.0 and newer

## Table of UUIDs

Name | UUID
----- | ---------------
Service | 000018aa-0000-1000-8000-00805f9b34fb
Characteristic for read | 00002bb0-0000-1000-8000-00805f9b34fb
Characteristic for write | 00002bb2-0000-1000-8000-00805f9b34fb
Characteristic for indicate | 00002bb1-0000-1000-8000-00805f9b34fb

## BLE Central (all platforms)

Central (also called Master or Client) works similarly on all platforms:

* Scans for Peripherals which have a service with our UUID (see Table of UUIDs)
* Connects to the first found Peripheral
* Discovers services and characteristics of the connected Peripheral
* Subscribes to indications of the "Characteristic for indicate" (see Table of UUIDs)
* Allows the user to disconnect from Peripheral
* Allows the user to read a characteristic value (string) from Peripheral
* Allows the user to write a characteristic value (string) to Peripheral

The App will start the central, discover the services + Characteristics, connect to the peripheral, read a value, request to be notified for value update, write a value.

I have attached the DEMO source code of 2 project. The Central source simulate the iOS Device and the Peripheral source simulate the Bluetooth device with specify service and characteristic in the Table UUID.

We have a lot of functions detail in the source code and here are some important functions I want to note with you.

## IN BLEProofCentral SOURCE

* App request permission for Bluetooth event. for that, in info.plist, I added this :

```
    <key>NSBluetoothAlwaysUsageDescription</key>
    <string>We use Bluetooth to show basic communication between Central and Peripheral</string>
    <key>NSBluetoothPeripheralUsageDescription</key>
    <string>We use Bluetooth to show basic communication between Central and Peripheral</string>
    <key>UIApplicationSupportsIndirectInputEvents</key>
```

* Init BLE

```swift
    private func initBLE() {
        // using DispatchQueue.main means we can update UI directly from delegate methods
        bleCentral = CBCentralManager(delegate: self, queue: DispatchQueue.main)
    }
```

* BLELifecycleState

```swift
    enum BLELifecycleState: String {
    case bluetoothNotReady
    case disconnected
    case scanning
    case connecting
    case connectedDiscovering
    case connected
    }
```

When scan and connect the central to peripheral, implement count down 30s timeout.

* Count down time

```swift
    private func startCheckError(duration: Int = 30) {
        cancelTimer()
        countDownNumber = duration
        timer = Timer.scheduledTimer(timeInterval: 1,
                                     target: self,
                                     selector: #selector(updateTime),
                                     userInfo: nil,
                                     repeats: true)
    }
    
    private func cancelTimer() {
        if let _ = self.timer {
            self.timer!.invalidate()
            self.timer = nil
        }
    }
    
    @objc func updateTime() {
        if countDownNumber <= 0 {
            finishTimer()
            return
        }
        countDownNumber -= 1
    }
    
    private func finishTimer() {
        cancelTimer()
        print("stage ==== \(lifecycleState)")
        if lifecycleState == .scanning {
            showAlertRetry(title: "Notification", message: "Connect Fail, plz retry it.") {
                self.switchConnect.isOn = false
            } retryAction: {
                self.bleScan()
            }

        }
    }
```

* Handle data recevice from bluetooth device (peripheral)

```swift
    func peripheral(_ peripheral: CBPeripheral, didUpdateValueFor characteristic: CBCharacteristic, error: Error?) {
        guard error == nil else {
            appendLog("didUpdateValue error: \(String(describing: error))")
            return
        }
        
        let data = characteristic.value ?? Data()
        let stringValue = String(data: data, encoding: .utf8) ?? ""
        if characteristic.uuid == uuidCharForIndicate {
            handleDataNotify(data)
        }
        appendLog("didUpdateValue '\(stringValue)'")
    }
```

* Function write and read Characteristic

```swift
    func bleReadCharacteristic(uuid: CBUUID) {
        guard let characteristic = getCharacteristic(uuid: uuid) else {
            appendLog("ERROR: read failed, characteristic unavailable, uuid = \(uuid.uuidString)")
            return
        }
        connectedPeripheral?.readValue(for: characteristic)
    }
    
    func bleWriteCharacteristic(uuid: CBUUID, data: Data) {
        guard let characteristic = getCharacteristic(uuid: uuid) else {
            appendLog("ERROR: write failed, characteristic unavailable, uuid = \(uuid.uuidString)")
            return
        }
        connectedPeripheral?.writeValue(data, for: characteristic, type: .withResponse)
    }
```

Convert and handle data send to the Peripheral and receive from Peripheral

* Data send

```swift
    let text = textFieldDataForWrite.text ?? ""
        if let data = text.data(using: .utf8) {
            bleWriteCharacteristic(uuid: uuidCharForWrite, data: data)
        }
```

* Data receive notification

```swift
    private func handleDataNotify(_ data: Data) {
        var textJson = String(data: data, encoding: .utf8) ?? ""
        if let indexRemove = textJson.firstIndex(where: { $0 == "<" }) {
            textJson.remove(at: indexRemove)
        }
        if let indexRemove = textJson.firstIndex(where: { $0 == ">" }) {
            textJson.remove(at: indexRemove)
        }
        guard let data = textJson.data(using: .utf8),
              let json = try? JSONSerialization.jsonObject(with: data) as? [String: Any],
              let result = json["result"] as? String
        else {
            showAlert(title: "Data Send", message: "FAIL")
            return
        }
        showAlert(title: "Data Send", message: result == "ng" ? "FAIL" : "SUCCESS")
    }
```

* Define format data send to the Peripheral

```swift
enum DataSendDummy: Int {
    case success = 0, fail
    
    var json: String {
        switch self {
        case .success:
            return "<{\"thingName\":\"Daikin_d813997f4904\",\"action\":\"bleconfig\",\"ssid\":\"HUAWEI-1CAFB0\",\"password\":\"1\",\"setkey\":\"cfe18ee376b5fb4b14245ad92f167787\"}>"
        case .fail:
            return "<{\"thingName\":\"Daikin_d813997f4904\",\"action\":\"bleconfig\",\"ssid\":\"HUAWEI-1CAFB0\",\"password\":\"2\",\"setkey\":\"cfe18ee376b5fb4b14245ad92f167787\"}>"
        }
    }
}
```

## BLE Peripheral (all platforms)

Peripheral (also called Slave or Server) works similarly on all platforms:

* Advertises a service with our UUID (see Table of UUIDs)
* The service contains 3 characteristics:
  * for read - has only read permission (see Table of UUIDs)
  * for write - has only write permission (see Table of UUIDs)
  * for indication - supports only indications (see Table of UUIDs)
* Allows the user to change the string value of the characteristic for read
* Allows the user to change the string value of the characteristic for indicate
* Allows the user to send an indication with updated string value to the connected Central

Note 1: technically characteristics can have any amount of permissions (read, write default, write without response, notify, indicate), but in this project each characteristic has only one permission for simplicity.

Note 2: indication is a notification with response - Peripheral notifies, Central confirms that notification received.

## IN BLEProofPeripheral SOURCE

* Build BLE Service
* 
```swift
private func buildBLEService() -> CBMutableService {

        // create characteristics
        let charForRead = CBMutableCharacteristic(type: uuidCharForRead,
                                                  properties: .read,
                                                  value: nil,
                                                  permissions: .readable)
        let charForWrite = CBMutableCharacteristic(type: uuidCharForWrite,
                                                   properties: .write,
                                                   value: nil,
                                                   permissions: .writeable)
        let charForIndicate = CBMutableCharacteristic(type: uuidCharForIndicate,
                                                      properties: .indicate,
                                                      value: nil,
                                                      permissions: .readable)
        self.charForIndicate = charForIndicate

        // create service
        let service = CBMutableService(type: uuidService, primary: true)
        service.characteristics = [charForRead, charForWrite, charForIndicate]
        return service
    }
```

* Handle data reviece from BLE Central

```swift
 private func handleDataResponse(_ dataResponse: Data) {
        var textJson = String(data: dataResponse, encoding: .utf8) ?? ""
        if let indexRemove = textJson.firstIndex(where: { $0 == "<" }) {
            textJson.remove(at: indexRemove)
        }
        if let indexRemove = textJson.firstIndex(where: { $0 == ">" }) {
            textJson.remove(at: indexRemove)
        }
        convertToJson(with: textJson)
    }
    
    private func convertToJson(with text: String) {
        guard let data = text.data(using: .utf8),
              let json = try? JSONSerialization.jsonObject(with: data) as? [String: Any],
              let pass = json["password"] as? String
        else {
            sendNotify(isResponseSuccess: false)
            return
        }
        sendNotify(isResponseSuccess: pass == "1")
    }
    
    private func sendNotify(isResponseSuccess: Bool) {
        let textSuccess = "<{\"action\":\"bleconfig\",\"result\":\"ok\"}>"
        let textFail = "<{\"action\":\"bleconfig\",\"result\":\"ng\"}>"
        bleSendIndication(isResponseSuccess ? textSuccess : textFail)
    }
```

* Function didReceiveWrite will receive data from BLE Central

```swift
    func peripheralManager(_ peripheral: CBPeripheralManager, didReceiveWrite requests: [CBATTRequest]) {
        var log = "didReceiveWrite requests.count = \(requests.count)"
        requests.forEach { (request) in
            log += "\nrequest.offset: \(request.offset)"
            log += "\nrequest.char.UUID: \(request.characteristic.uuid.uuidString)"
            switch request.characteristic.uuid {
            case uuidCharForWrite:
                if let data = request.value {
                    handleDataResponse(data)
                    let textValue = String(data: data, encoding: .utf8)
                    log += "\nresponding with success, value = '\(String(describing: textValue))'"
                    blePeripheral.respond(to: request, withResult: .success)
                }
            default:
                log += "\nresponding with attributeNotFound"
                blePeripheral.respond(to: request, withResult: .attributeNotFound)
            }
        }
        appendLog(log)
    }
```

* When receive data from BLE Central, BLE Prepheral will notify success or fail to BLE Central

```swift
    private func bleSendIndication(_ valueString: String) {
        guard let charForIndicate = charForIndicate else {
            appendLog("cannot indicate, characteristic is nil")
            return
        }
        let data = valueString.data(using: .utf8) ?? Data()
        let result = blePeripheral.updateValue(data, for: charForIndicate, onSubscribedCentrals: nil)
        let resultStr = result ? "true" : "false"
        appendLog("updateValue result = '\(resultStr)' value = '\(valueString)'")
    }
```

## Recommended resources

iOS:

* [Transferring Data Between Bluetooth Low Energy Devices](https://developer.apple.com/documentation/corebluetooth/transferring_data_between_bluetooth_low_energy_devices) by Apple (with sample code, Central and Peripheral)
* [The Ultimate Guide to Apple’s Core Bluetooth](https://punchthrough.com/core-bluetooth-basics/) by PunchThrough
* [Core Bluetooth Tutorial](https://www.raywenderlich.com/231-core-bluetooth-tutorial-for-ios-heart-rate-monitor) by Raywenderlich

## Demo
![alt text](https://i.imgur.com/3lyWVLq.gif)
