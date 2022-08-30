---
tags: iOS, MacOS, Swift
author: Phan Viet Trung
---

In the last article `How can we build a UI using Builder pattern`, we are build the UIKit components by using builder pattern. This is the second part `How can we wrap the container element using Swift builder`. Feel free to read it before we are continue on this.
<https://github.com/dwarvesf/brain/blob/master/Engineering/Mobile/UIKit%20Builder%20pattern.md>

## How can we wrap the container elements using Swift builder?

### Function Builder

Function Builders introduced in Swift 5.1 to support SwiftUI. If you heared about VStack it builded using Function Builder.

```Swift
VStack {
    Text("Hello world")
    Text("Dwarves Foundation Better Engineering")
}
```

### `@resultBuilder`

Swift 5.4 make it even better with the introduce of @resultBuilder. It's not only the foundation of SwiftUI but also extend DSL to standard Swift language. You can apply it anywhere to take advantage of DSL.

More details at: <https://github.com/apple/swift-evolution/blob/main/proposals/0289-result-builders.md>

From now on you can easily write HTML form with Swift like this:

```Swift
HTML {
    Body {
        P { "Hello HTML" }
        DIV { 
            P{}
            P{}
            DIV{}
         }
    }
}
```

Let extend our UIKit to write an UI in DSL style.
In the last article we using Builder Pattern to archived UILabel().text("ABC").textColor(.red), let's add a container View to make it even better.
UIKit have Stack View, Stack view hepling us to arrange subviews by horizontaly or vertially.

Let make it

From:

```Swift
let label = UILabel().text("ABC").backgroundColor(.red)

let stackView = UIStackView()
stackView.distribution = .center
stackView.axis = .horizontal
stackView.addArrangeSubview(label)
```

To:

```Swift
UIHStack {
    UILabel().text("ABC").backgroundColor(.red)
}
```

### Turn UIKit into DSL styling

Let define our base UIViewBuilder. UIViewBuilder turn DSL UIView into list of UIView.

```Swift
@resultBuilder
public enum UIViewBuilder {
    public static func buildBlock(_ components: UIView...) -> [UIView] {
       components
    }
}
```

Use:

```Swift
let views = UIViewBuilder.buildBlock(UILabel(), UIImageView(), UIView())
@UIViewBuilder func createUI() -> [UIView] {
    UILabel()
    UIImageView()
}
```

**Note:** You may asking "Why is the return type is [UIView] instead of UIView ?" I will explain it later.

With above UIViewBuilder we get a array of views from DSL syntax. It helping us write the code naturally without constaly write addSubview code.

We can write in DSL style but above code look not cool at all. Let's write some popular UI
wrapper for convenience use.

```Swift
public class UIVStack: UIStackView {
    public convenience init(@UIViewBuilder _ builder: () -> [UIView]) {
        self.init(arrangedSubviews: builder())
        self.distribution = .fill
        self.spacing = 16
        self.axis = .vertical
    }
}
```

Now we have convenience UIVStack:

```Swift
UIStackView {
    UILabel()
    UIImageView()
    UITextField()
}
```

As you can see, using array of UIView instead of UIView we can add them to StackView instead of call `addSubView` multiple times.

Let's add some more components.

```Swift
public class UIHStack: UIStackView {
    public convenience init(@UIViewBuilder _ builder: () -> [UIView]) {
        self.init(arrangedSubviews: builder())
        self.distribution = .fill
        self.spacing = 16
        self.axis = .horizontal
    }
}

public class UIZStack: UIView {
    convenience init(@UIViewBuilder _ builder: () -> [UIView]) {
        self.init()
        builder().forEach { view in
            self.addSubview(view)
            view.translatesAutoresizingMaskIntoConstraints()
            view.fitToSuperView()
        }
    }
}
```

With the technique in the last article mix with `@resultBuilder` we can fully write UI using UIKit just like SwiftUI

<p align="center">
 <img src="../../_assets/ios_uikit_builder_pattern_banner.png" width="350">
</p>

```Swift
UIZStack(spacing: 16) {
    UIVStack(spacing: 16) {
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
            .mintStyle()
            .title("Update Now")
            .tap(action: { [weak self] in
                navigateToAppStore()
            })
            .heightAnchor(height: 44)
    }
}

```

### Bonus parts

**Support `if-else` and `loop`**

`@resultBuilder` have static function `buildEither` helping you add `if-else` stagement to DSL as well as `builderArray` heping you add looping to DSL.
The define just like a `buildBlock`:

```Swift
public static func buildEither(first component: [UIView]) -> [UIView] {
}
public static func buildEither(second component: [UIView]) -> [UIView] {
}
public static func buildArray(_ components: [[UIView]]) -> [UIView] {
}
```

```Swift
UIHStack {
    if true {
        UIView().backgroundColor(.red)
    } else {
        UIView().backgroundColor(.green)
    }

    for image in images {
        UIImageView(image: image)
    }
}
```

**Config container:**

Adding config to the init to settings container view.

```Swift
public class UIVStack: UIStackView {
    public convenience init(alignment: UIViewAlignment = .center, spacing: CGFloat = 16,  @UIViewBuilder _ builder: () -> [UIView]) {
        self.init(arrangedSubviews: builder())
        self.distribution = .fill
        self.spacing = spacing
        self.alignment = alignment
        self.axis = .vertical
    }
}

UIHStack(alignment: .trailling, spacing: 8) {

}
```
