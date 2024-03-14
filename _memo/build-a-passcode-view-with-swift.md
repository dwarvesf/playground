---
tags: 
  - swift
title: Build A Passcode View With Swift
date: 2019-06-22
description: null
authors: null
menu: memo
type: null
hide_frontmatter: false
---

![[38059dcec9bd2edb9ac9b1433eb8870c_MD5.webp]]

The highlights before we are write our code.

* Our Passcode view can “becomeFirstResponder” and “resignFirstResponder” to show and hide virtual keyboard if needed.

\=> Our Passcode nearly same with TextField.

Define our passcode view:

![[d816501201514ad7e20b8a1eaa11336b_MD5.webp]]

By default, to show keyboard on the screen user should touch in TextField or TextView to edit. We can make our custom view as keyboard input view by override “canBecomeFirstReponder” method and conform to UIKeyInput Protocol

![[e3aac2ef700961b85e15edbeba660e97_MD5.webp]]

![[e1f29ff96dcff1eabdaa75703feccaa7_MD5.webp]]

Now our view can show keyboard, you can test it by call passcode.becomeFirstResponder()

![[3af95d69a2b12d37965a6390e9ffc9e3_MD5.webp]]

![[af46d74372514e5a70b084d86b836f5e_MD5.webp]]

To help user easy using our passcode view we can add a tap gesture and call becomFirstReponder() to show keyboard. Now you can easy tap to show keyboard.

![[f2662e927b3487cb814b59e5b4fb6ab7_MD5.webp]]

Now we are going to build our logic to handle user input. There are 3 methods we need focus:

![[e1f29ff96dcff1eabdaa75703feccaa7_MD5.webp]]

Now append or delete our code string if needed.

![[1ca05e855a002b1a9b9062933c0637c3_MD5.webp]]

Greet, our passcode logic finished, the next challenge is map our code to PIN UI when code changed

Add an UIStackView to our Passcode view. Stack will distribute “Dot View” as Pin.

![[dc6fae0f3fb25101d24553d424836965_MD5.webp]]

![[36906b8962ed020434fa08918abb4452_MD5.webp]]

Create our Pin View

![[9538b2b34f1286a8dc0ea3af0754f8e6_MD5.webp]]

Create two more helper methods to create emptyPin and normal pin

![[9f05b8d51b192d5084b13c8c58a5f154_MD5.webp]]

Map user input code to Array of Pin views and distribute to stack

![[bb4c7b4c744eb9753d14c80f90713861_MD5.webp]]

The helper method to remove all add Arranged sub view from stack

![[d44d2498c831ac60ddbf0a53d5f34234_MD5.webp]]

Call our update stack when code changed

![[f4f7c7feb4ec4c1c638d716f2d270e5a_MD5.webp]]

Create ViewController to test our stack:

![[0f668d3c9f621a372a90657247d08e3a_MD5.webp]]

Make our PasscodeView conform to UITextInputTraints to able to set keyboard to numPad

![[c7b65095335c11d1ffa2865322c3e686_MD5.webp]]

Result

![[e0a5e31e6ae8c460f9968793cf29003e_MD5.webp]]

Add a callback when user finished input.

![[804017aefbe5ae510c9ea2cc7445e8f8_MD5.webp]]

![[383a2f3f5d10e682fdb546b70166a178_MD5.webp]]

Full source code at:
[https://github.com/viettrungphan/Passcode.git?source=post_page-----a6ddae69f405----------------------](https://github.com/viettrungphan/Passcode.git?source=post_page-----a6ddae69f405----------------------)

Please notice the project written by Xcode 11 beta. Your can simple copy all Prefix Passxxx and Pin files to your xcode project to test.
