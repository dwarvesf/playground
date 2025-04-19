---
tags: 
  - frontend
  - engineering
  - radio
title: React Native New Architecture
date: 2022-06-14
description: null
---

Introducing react-native's new architecture changes that boost performance, bringing react-native back into the race with Flutter

![](assets/react-native-new-architecture_ca02c7ac30b22ad423bf3285f8cdaa16_md5.webp)

## Introduction of react-native
>
> React Native is a JavaScript framework for writing high-performance mobile apps that leverage iOS and Android native components. It is based on React, and is very accessible to React Web developers

After a long announcement, planned from 2018, appeared in 2020, merged in 2021 and officially published in April 2022, react-native has a new architecture that improves performance dramatically. excel, helping it get back into the cross-platform app development race with Flutter.

We will find out what changes this new architecture have made to improve the performance of the application, and whether we should upgrade to this new version right away.

The content of the post will include the following main sections:

1. **Old architecture of react-native
1. **What's new in New Architecture
1. **Fabric - JSI - Turbo module  
1. **Migrate to the new architecture?

## Old architecture of react-native

Basically, the old react-native architecture was standing on 3 threads running in parallel

![](assets/react-native-new-architecture_be56fa7f4ae19c9284e37e61706d1133_md5.webp)

1. **JavaScript thread:** Where the JS code is read and compiled and where the React Native app business logic is handled
2. **Native UI thread:** Responsible for the app's UI, this is where the native code is executed
3. **Shadow thread**: Where React Native calculates your app's layout using Facebook's Yoga (its own layout engine), which turns flexbox-based styles and turns them into native height, spacing, width...

![](assets/react-native-new-architecture_00906c2cfe7b99ad8994125f2dad50e8_md5.webp)

## Cause of congestion, slowness, frame drop Bridge  

In order to make the communication between the Native and the JS thread possible, you had to use a C++ module: Bridge.

**Here's how it works:**

1. Each time it receives data from the Native or the JS thread
2. It serializes it as JSON
3. Sends it to the queue
4. And decode upon arrival.

***This bridge-based structure is prone to delays.***

Threads based on a JSON signal stream get sent over a Bridge asynchronously, but certain events on the JS thread can block the UI events.

![](assets/react-native-new-architecture_044af91a93a00b09540b03b991e4e32a_md5.webp)

## What's new in New Architecture

![](assets/react-native-new-architecture_fb23cab260bd0ec3a95ac7d6a69c461a_md5.webp)

* **Fabric:** Fabric is the rendering system, which will replace the current UI Manager.
* **JSI:** JavaScript Interface, general-purpose layer, written in C++ can be used by the JavaScript engine to directly invoke/call methods in the native realm.
* **Turbo modules:** This will significantly improve startup time for ReactNative apps.

## Fabric

* Fabric is the rendering system, which will replace the current UI Manager.
* The Fabric renderer seeks to improve the interoperability of React Native with host platforms, which are responsible for embedding React Native in Android, iOS, macOS, Windows, etc.

![](assets/react-native-new-architecture_08f9602cedbc58744cf72fc3580bf068_md5.webp)

ReactElementTree (JavaScript) --> ReactShadowTree(C++) --> HostViewTree(Native)

## JSI - JavaScript Interface

Through the JSI, Native methods will be exposed to JavaScript via C++ Host Objects. JavaScript can hold a reference to these objects. And can invoke the methods directly using that reference.

* JavaScript has a direct reference to a native module
* It calls a method on this native module, via the JavaScript Interface

![](assets/react-native-new-architecture_1066bb62cbc4d9beda7e03d43006c669_md5.webp)

## Turbo modules

* Turbo Modules are basically an enhancement over these old Native modules
* JavaScript will be able to hold reference to these module
* Which will allow JS Code to load each module only when it is required. This will significantly improve startup time for react-native apps

![](assets/react-native-new-architecture_193938237761968661a5f11f23670f3d_md5.webp)

## The advantages of the New architecture

1. Huge performance gains for your react-native apps
1. Better app launch time
1. Shorter app development time
1. The possibility to use it for large system goals (with all that C++ power at your disposal)

# Should I migrate to the new architecture?

Not yet!

There are many libraries that support new architectures (Fabric not yet), for example reanimated library is an important animation library in react-native community, it doesn't support Fabric yet leading to many other UI libraries like gorhom/react-native-bottom-sheet also get error.

My project that uses react-native-maps on android (AirMap in native) also doesn't support Fabric so it also got an error, forcing me to disable the new architecture. At the same time, the FlexBox layout on version 0.68.0 is also unstable. So my advice to you is if your project is in a rush, it's not a great time to update it to a new architecture, we should wait for the next 1 or 2 version. (0.69.x) is much more stable and bug-free, and other libraries also support the new architecture for better performance.

If you want to try something new on your personal project, you can update right away.
