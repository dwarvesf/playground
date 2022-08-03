---

tags: iOS, MacOS, Swift

author: Phan Viet Trung

---
## UIKit builder pattern.

With the UIKit, to write a simple Login form we're usually do:
```
let txtUserName = UITextField()
txtUserName.placeHolder = "User Name"
txtUserName.textColor = .black8
//For text change event.
txtUserName.delegate = self 

let txtPassword = UITextField()
txtPassword.placeHolder = "Password"
txtPassword.textColor = .black8
//For hide password
txtPassword.stype = .password
txtPassword.delegate = self
```


For the small project, it totally fine. However with large project, we have a standard design. How can we reuse our code, keep it simple to use, and keep a flexility.

Normally we will override the Original data type and create our own components following the style that designer give us.

ex:
```
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



Everything is ok then one day designer give us new page with diffirent text, background color, different font size.

We are continue create a new MyStyleRedTextField
With above implementation we can reuse our code but lossing the fexiblity of customize. How can we fix it?

One way is using config like:
```

let textField = UITextField()
textField.config(textColor: .red, font: .system, backgroundColor: .white)

extension UITextField {
	func config(textColor: UIColor, font: UIFont, backgroundColor: UIColor) {
		//set
	}
}

```
The question is: What if I need to custom other properties of UITextField. Add a new config function? How to sync with design and reuse code?

**Introduce to `@discardableResult`.**

Swift programming language has @discardableResult. The beauty of @discardableResult is you can use or unuse the return value of the function without compiler, editor complaint.

For example:
We have a function that return a String
```
func hello() -> String {
	"Hello"
}
```

use:
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

hello() <- No warning
let helloString = hello() <- Can assign value

```

**Introduce to `Extension`**
The iOS-MacOS developer is family with `Extension`. With Extension we can add more functionality to existed Object.

ex:

```
Extension UILabel {
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

```
Extension UILabel {
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
```
let label = UILabel()
					.textColor(.red)
					.text("Hello")
```
Becase `label` just a UILabel, you can still use any buildin properties, methods.
Like access to get infos, set new property.
ex: 
```
let text = label.text
let background = text.backgroundColor

label.text = "ABC"
```
To create you style simple by extend it using the same technique 

```
Extension UILabel {
	@discardableResult
	func myRedStyle() -> UILabel {
		self.textColor(.red).backgroundColor(.green)
		return self
	}
}

let redLabel = UILabel().text("I'm red").myRedStyle()
```

Adding more function to `Extension` with `@discardableResult` we have all benefits of reuse, flexible, easy to use, easy to maintain, expand our code as well as keep original data type.