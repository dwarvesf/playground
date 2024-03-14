---
tags: 
  - swift
title: Create Circular Text Using Swiftui
date: 2020-03-23
description: null
authors: null
menu: memo
type: null
hide_frontmatter: false
---

![[6872696f92cc278214818c3e90f67383_MD5.webp]]

This is what we have when finished.

Fire up your Xcode and create new SwiftUI Project.

Create new SwiftUI file and named it CircularText.

The first two attributes for our control of course is String and Radius for our circular.

Add 2 Attribute named

![[9b6a81fbaea69fbc04804680517f7628_MD5.webp]]

To make a circle text we split out string to array of character, each character will have it own Text control then we going to rotate the text to match circle.

Define computer property to split string to array of character:

![[46724b5601eab5c6899e4444f5729480_MD5.webp]]

Using enumerated to get offset using later.
To calculate angle using to make rotation later we need 2 things: perimeter of circle and width of each character.

![[d850c4e1905c1fe203887a585b99beb0_MD5.webp]]

Later we will use it as radius.perimeter

For Width of each character is a bit complicate. We need place it in some control and get size of that control somehow. Text is the best candidate for this case.

Embed Text and Spacer in Vstack we have a custom control as tall as parent view and the text at top of control, this make us easy to make rotation later because we just need rotation at center of control.

![[c8ece1efb4286be7223bcb132a0e1257_MD5.webp]]

Now we have List of Text, the next thing is get it width value. SwiftUI let us get size from control using GeometryReader, and we send it to outside using PreferenceKey

![[1f272824a0e403cad5a4d5a45fe5c91f_MD5.webp]]

We going to place custom Sizeable View as background of Text, because Sizable View actually a Color, it going to fill the parent (which is background of Text)so we got exactly size of Text
To store that sizes let add a Dictionary to save it, the key will be the position of Character. Add a dictionary named textSizes

![[9f748f21526907df2f65cfa50b2b3526_MD5.webp]]

Update our VStacks to save sizes when preference changed

![[068016d599ac0fe7ebeb1c320496fea9_MD5.webp]]

We have perimeter and with of each character, now calculate angle of each character by it position

![[62ae3eea7d36359b7e26f8840a74dd3d_MD5.webp]]

This function simple calculate how many percentages of size.with compare to perimeter of circular, then figure out angle by that percent.

We have angle, now make rotation and see results:

![[f9fb1ddc68ddef8e0c9f6f321e34aaeb_MD5.webp]]

Look like the space between characters have problem. This because of it just fit enough for horizontal Text, when we make circle, the rotation angle make it close together. Luckily the building kerning Modifier make us easily to adjust it.

![[fdd18ae3a8fd903729c18eda97d7ae1f_MD5.webp]]

If you want to make it center, simple ask the angle of last character divide by 2 then rotation it anticlockwise.

![[1f24f4e09d557c69ef6b57fcc4e0ab66_MD5.webp]]

We are done, hope you enjoy and have fun with SwiftUI.

View more at: [https://github.com/viettrungphan/SwiftUIGeometryPractice](https://github.com/viettrungphan/SwiftUIGeometryPractice)
