---
tags: 
  - swift
title: Draw Watch Face Using Swiftui
date: 2020-03-23
description: null
authors: null
menu: memo
type: null
hide_frontmatter: false
created: 2020-03-23
---

SwiftUI are nice and fun to working with. You can read my previous article to get a bit knowledge about create circular control, it will make you easy to working with this article. This article also use Shape and Path, if you have worked with CoreGraphic before you will find it similar With CALayer, CAShapeLayer and UIBezierPath.

> Create Circular Text using SwiftUI

First of all, let split watch to small components for easy coding. A watch has these following parts:

* *Circular Bezel*
* *Ticks-Markers*
* *Hour, Minus, Second hands.*
* *Number markers. from 1 to 12*

As usual, open Xcode and create new project, don’t forget to choose SwiftUI, add new SwiftUI file and named it Watch.

### Draw Circular Bezel
Path is similar to BenzierPath, you can draw Oval, rectangle, line, arc using Path.
I choose Arc for now. Later on we can using Arc, Oval or Circle to make different watch face style.
Add a new struct and named it Arc conform to Shape protocol.
Xcode will guild you add missing path method to conform with Shape.

Path methods provided us rect which is the frame we are using to draw on it.
the Act function required center point, starting angle and ending angle, we need complete circle so let start with 0 and end with 2pi which 2 angle of circle in radiants

![[9054ef9952d75edd68df70ced08a4374_MD5.webp]]

![[76624a28445c749c81b50d7c39444ac1_MD5.webp]]

Try our new Arc struct, nice we have a black circle, you can try replace stroke(lineWidth) by fill() and see what happened, also try different starting and ending angle to see what happened.

### Draw Ticks-Markers
Create new Struct Named Tick, it also conform to Shape.
This tick shape simple draw a line front top center down to 5 points

![[6fd475833c3e5bf231d0a1b5c66f36a1_MD5.webp]]

Try out our new Tick, also embed all of them inside ZStack and give frame to make all view inside Stack have same size.

![[02b6127060bc0a8b7b2ed8f9e27932d9_MD5.webp]]

Our next job is simple, just repeat 60 times and rotated it.
The angle for each tick just a circle divided by 60 (2pi/60)
For readable and maintainability, I create new view named Ticks for it.

![[825170f610ff118e6ca60e6a20bf6673_MD5.webp]]

This is What we have after repeat 60 time.

![[9893a8992e67501a431b66be2f573212_MD5.webp]]

However at 5, 10, 15, 20… minutes we should make tick a bit longer.
Let change our Tick and Ticks View a bit to add this extra.

![[db13dc3f187742fbc3806a3faf95c321_MD5.webp]]

We have finished draw ticks, let move on hour Numbers.

### Draw Numbers
This use the same technique with [my previous article](https://medium.com/@phanviettrung/create-circular-text-using-swiftui-32cd7e5b6414), feel free to read it.

Basically we create a VStack with Text and Spacer to make the text at alignment top and as tall as parent view. This trick helping us easy to rotate the texts and keep the same radius.

![[bf7e847b9d6f525d83c00b064178362b_MD5.webp]]

Just like Tick, we repeat it 12 times, because number in Watch show from 1 to 12, I use 1 -> 13 instead of 0 -> 12

![[ec7fa0f45d8d452407b23dd299ba4df1_MD5.webp]]

Try it and We got beautiful numbers indicator.

![[135752868b2e9b57c2e9b252a68d6a2d_MD5.webp]]

### Draw Hour, Minus, and Second Hands
Make a pad circle for our Watch Hands. This completed by helping of building circle

![[d61b193f367f89629d4d3f4637001158_MD5.webp]]

Now the Hand, we draw a round rectangle from center to some where between center and top, depending on it is an hour, a minus or a second hand.

Create new Shape, named Hand, to adjust height we adding offset property

![[8e0070c6558d165208af627d5d128e30_MD5.webp]]

![[17aa6318aafb9fff34aaa10f6d38cfd1_MD5.webp]]

Test minute hand, using frame width to adjust how wide it will.

![[677b0fdbf3eddf813c65c1a4b03facc8_MD5.webp]]

Now repeat with hour and second hand

![[cf25ca4271503a2598b2ee327ca1c5a1_MD5.webp]]

It hard to see because it overlapping each other. You can use debug view hierarchy view to verify it.

![[c518a8b09cd378ce2277c834453383fa_MD5.webp]]

We are not finished yet, our watch look better if we add a red dot for second hand.

![[086f194966e7d9ea5915a6c1fe7b0be0_MD5.webp]]

We are finished our Watch View but let it “run-able” by make hands tick real time.

Add a date State property wrapper. We will update this property each one second, Hour, Minus and Second hand will know this change and make adjustments.

![[befcff914e798c46c4244d1dffbb5282_MD5.webp]]

Add a method to automatically update “date” variable.

![[11774d63139169af2acacd716157c8dd_MD5.webp]]

Call this on view appear event of ZStack

![[0f17e4f9c09fda63825ec1414269213e_MD5.webp]]

The final thing is base on current date time, we calculate an angle for hour, minus and second hand

![[4f565c4cc944f29623fe1fb8a9255d11_MD5.webp]]

The code is it self explanatory, I don’t have anything else to tell you.

Now use angles above to make our hands rotation

![[cfad5beb3ea58b7d6432a569afb0caf9_MD5.webp]]

Congratulations, our watch now run as normal watch.

![[397bf52e863bd1e23b8d6ba2f5f11154_MD5.webp]]

### Bonus part
You can change Arc to Circle, mix with different color to get more watch face

![[8650c87b9f9651707bb5969d0d0fbe6d_MD5.webp]]

View more at: [https://github.com/viettrungphan/SwiftUIGeometryPractice](https://github.com/viettrungphan/SwiftUIGeometryPractice)
