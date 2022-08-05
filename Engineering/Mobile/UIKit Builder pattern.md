---

tags: iOS, MacOS, Swift, UIKit

author: Phan Viet Trung

---

SwiftUI introduces a declarative way to write UI. Can we use the same paradigm with UIKit?
We will show you how. There are two parts of this tutorial.

The first part is: `How can we build a UI using Builder pattern` and second part is `How can we wrap the container element using Swift builder`.

In the end of the serials you can build UI like this:
<p align="center">
	<img src="../../_assets/ios_uikit_builder_pattern_banner.png" width="350">
</p>

By below sample code:

```swift
let vStack = UIVStack {
    UIImageView(image: UIImage(named:"banner"))
    UIView()
        .backgroundColor(.clear)
        .heightAnchor(height: 20)
    UILabel()
        .text(title)
        .font(UIFont.systemFont(ofSize: UIFont.largeSize))
        .textAlignment(.center)
        .color(.black60)
    UILabel()
        .text(subtitle)
        .font(UIFont.systemFont(ofSize: UIFont.normalSize))
        .textAlignment(.center)
        .color(.black60)
        .numberOfLines(0)
    
    UIButton()
        .spStyle()
        .title("Update Now")
        .tap(action: { [weak self] in
            self?.navigateToAppStore()
        })
        .heightAnchor(height: 44)
}


```



### **How can we build a UI using Builder pattern**

With the UIKit, to write a simple Login form we're usually do:

```swift
let txtUserName = UITextField()
txtUserName.placeHolder = "User Name"
txtUserName.textColor = .black8
//For text change event.
txtUserName.delegate = self 

let txtPassword = UITextField()
txtPassword.placeHolder = "Password"
txtPassword.textColor = .black8
//For hide password
txtPassword.style = .password
txtPassword.delegate = self
```


For the small project, it totally fine. However, with a large project, we have a standard design. How can we reuse our code, keep it simple to use, and keep flexible?

Normally we will override the Original data type and create our own components following the style that the designer gives us. For example:
```swift
class MyStyleBlackTextFiled: UITextField {
    func setupUI() {
        self.textColor = .black8
        self.font = UIFont(systemFontOfSize: 18)
        self.backgroundColor = .white
    }
}


let txtUserName = MyStyleBlackTextFiled()
let password = MyStyleBlackTextFiled()

```

Everything is fine until one day the designer gives us a new page with different text, background color, different font size.

We are continue create a new `MyStyleRedTextField`
With the above implementation, we can reuse our code but losing the flexibility of customisation. How can we fix it?

One way is using config like:
```swift
let textField = UITextField()
textField.config(textColor: .red, font: .system, backgroundColor: .white)

extension UITextField {
    func config(textColor: UIColor, font: UIFont, backgroundColor: UIColor) {
        //set
    }
}

```
The question is: What if we need to custom other properties of `UITextField` or add a new config function? How to sync with design and reuse code?

### **Introduce to `@discardableResult`.**

Swift programming language has @discardableResult. The beauty of @discardableResult is you can use or unuse the return value of the function without compiler, editor complaint.

For example:
We have a function that return a String
```swift
func hello() -> String {
	"Hello"
}
```

Use:

`hello()` <-- The editor will warning you hello() is unuse.

To silent it we can using `_` to silent:

`_ = hello()`
or 
`let _ = hello()`

With @discardableResult:
```
@discardableResult()
func hello() -> String {
	"Hello"
}
```
Use:

`hello()` <- No warning

`let helloString = hello()` <- Can assign value



### **Introduce to `Extension`**

The iOS-MacOS developer is family with `Extension`. With `Extension`, we can add more functionality to the existing Object. For example:

```swift
extension UILabel {
    func textColor(_ color: UIColor) {
        self.textColor = color
    }
    func backgroundColor(_ color: UIColor) {
        self.backgroundColor = color
    }
}


use:
let label = UILabel()
label.textColor = .red
label .backgroundColor = .blue
```

**The Beauty of mixing `Extension` with `@discardableResult `= Builder**

```swift
extension UILabel {
    @discardableResult
    func text(_ string: String) -> UILabel {
        self.text = text
        return self
    }

    @discardableResult
    func textColor(_ color: UICOlor) -> UILabel {
        self.textColor = color
        return self
    }
}

```



With above implement we can archive:
```swift
let label = UILabel()
    .textColor(.red)
    .text("Hello")

```
Because `label` just a UILabel, you can still use any built-in properties, methods. Like access to get info, set new property. For example: 
```swift
let text = label.text
let background = text.backgroundColor

label.text = "ABC"
```
To create your style, simply make an extension using the same technique 

```swift
extension UILabel {
    @discardableResult
    func myRedStyle() -> UILabel {
        self.textColor(.red).backgroundColor(.green)
        return self
    }
}

let redLabel = UILabel().text("I'm red").myRedStyle()

```

Adding more functions to `Extension` with `@discardableResult` we have all benefits of reusability, flexibility, maintainability, and the ability to expand our code as well as keep the original data type.
