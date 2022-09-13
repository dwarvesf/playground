---
tags: engineering/mobile, flutter, stateless, statefull
author: Nguyen Tran Khanh
date: 2022-12-09
---

## State
> State: The State is the information that can be read synchronously when the widget is built and might change during the lifetime of the widget.  

State is something that can change within a widget. For example, let’s say we have a like button. The button can either be filled in, or not filled in depending on whether it has been clicked. That’s a state right there. The state of that button can either be filled in or not filled in. If a widget is constant and does not change no matter what is done, then it does not have a State.


## Stateless Widget
**Stateless Widget**: The widgets whose state can not be altered once they are built are called stateless widgets. These widgets are immutable once they are built i.e any amount of change in the variables, icons, buttons, or retrieving data can not change the state of the app. Below is the basic structure of a stateless widget. Stateless widget overrides the build() method and returns a widget. For example, we use Text or the Icon is our flutter application where the state of the widget does not change in the runtime. It is used when the UI depends on the information within the object itself. Other examples can be Text, RaisedButton, IconButtons.

```Dart
import 'package:flutter/material.dart';
 
//This function triggers the build process
void main() => runApp(const MyApp());
 
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        backgroundColor: Colors.blue,
        appBar: AppBar(
          leading: const Icon(Icons.menu),
          backgroundColor: Colors.green,
          title: const Text(
            "Dwarves Foundation",
            textAlign: TextAlign.start,
          ),
        ), // AppBar
        body: const Center(
          child: Text(
            "Stateless Widget Demo",
            style: TextStyle(color: Colors.black, fontSize: 30),
          ),
        ), // Container
      ), // Scaffold
    ); // MaterialApp
  }
```

## Statefull widget
**Stateful Widgets**: The widgets whose state can be altered once they are built are called stateful Widgets. These states are mutable and can be changed multiple times in their lifetime. This simply means the state of an app can change multiple times with different sets of variables, inputs, data. Below is the basic structure of a stateful widget. Stateful widget overrides the createState() and returns a State. It is used when the UI can change dynamically. Some examples can be CheckBox, RadioButton, Form, TextField.

Classes that inherit “Stateful Widget” are immutable. But the State is mutable which changes in the runtime when the user interacts with it.

```Dart
class MyApp extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return _MyAppState();
  }
}

class _MyAppState extends State<MyApp> {
  List<String> _fruits = ['Apple'];

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Demo Statefull')),
        body: Column(children: [
          Container(
              margin: EdgeInsets.all(10.0),
              child: RaisedButton(
                  onPressed: () {
                    setState(() {
                      _products.add('Orange');
                    });
                  },
                  child: Text('Dwarves Foundation'))),
          Column(
              children: _products
                  .map((element) => Card(
                        child: Column(
                          children: <Widget>[Text(element)],
                        ),
                      ))
                  .toList()),
        ]),
      ),
    );
  }
}
```

## Differences Between Stateless and Stateful Widget: 
**Stateless Widget:**  
  * Stateless Widgets are static widgets.
  * They do not depend on any data change or any behavior change.
  * Stateless Widgets do not have a state, they will be rendered once and will not update themselves, but will only be updated when external data changes.
  * For Example: Text, Icon, RaisedButton are Stateless Widgets. 


**Stateful Widget:**
  * Stateful Widgets are dynamic widgets.
  * They can be updated during runtime based on user action or data change.
  * Stateful Widgets have an internal state and can re-render if the input data changes or if Widget’s state changes.
  * For Example: Checkbox, Radio Button, Slider are Stateful Widgets