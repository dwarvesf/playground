---
tags: engineering, debug, console, debugger, javascript
author: Tran Hoang Nam
---
  This note focus on utilizing some of the **` console`** object methods and the **` debugger`** statement to better debug JavaScript application in the [Chrome DevTools](https://developer.chrome.com/docs/devtools/). 
  
## The `console` object
The **` console`** object provides access to the browser's debugging console. You can view it by right-clicking on your Chrome browser, selecting **Inspect**, and choosing **Console** in the tab.
![Chrome DevTools's console tab](https://wd.imgix.net/image/admin/Diu3Bq4TbPWb9Y5gr7HX.png?auto=format)

### `console.log()`
The `console.log()`  method writes to the web console. The message can be a single text (with optional replacement values) or any number of JavaScript objects.

#### Syntax
```js
console.log(obj1)
console.log(obj1, /* …, */ objN)
console.log(msg)
console.log(msg, subst1, /* …, */ substN)
```

#### Use-case
This method can be used to print any kind of variables defined before in it or to just print any message that needs to be displayed to the user.
```js
const name = "Dwarves Foundation";
console.log(name);
//=> Dwarves Foundation
```

### `console.assert()`
The `console.assert()` method writes a message to the console if an expression evaluates to `false`.

#### Syntax
```js
console.assert(_expression_, _message_);
```

#### Use-case
Let's say you wanted to check for a condition of a user id, you might be checking using the `console.log()` like this:
```js
if (!user.id){
	console.log("User does not exist!") \
	// user.id = false? => User does not exist!
}
```
Instead, you can check the condition using the `console.assert()`:
```js
console.assert(user.id, "User does not exist!") 
// user.id = false? => Assertion failed: User does not exist!
```
Using `console.assert()` provide a much cleaner and better way for conditional logging in your application.

### `console.dir()`
The `console.dir()` displays all of the properties of a specified JavaScript object in the console, allowing the developer to conveniently access the object's properties.

#### Syntax
```js
console.dir(object);
```

#### Use-case
In Chrome, `console.log` prints out a tree -- _most of the time_. However, Chrome's `console.log` still stringifies certain classes of objects, even if they have properties. A regular expression is the most obvious example of a distinction:
```js
const array = [1,2,3];
console.log(array);
// [1, 2, 3]
console.dir(array);
/* Array[3]
    0: 1
    1: 2
    2: 3
    length: 3
    * __proto__: Array[0]
        concat: function concat() { [native code] }
        constructor: function Array() { [native code] }
        entries: function entries() { [native code] }
        ... */
```
Another useful difference in Chrome exists when sending **`DOM`** elements to the console:
![console.dir() example](https://pbs.twimg.com/media/Di30ycpW0AAYOx7.jpg:medium)

### `console.time()` and `console.timeEnd()`
The `console.time()` method launches a timer that you may use to track the duration of the operation. You may have up to 10,000 timers running on a single page, giving each one a unique name. When you use `console.timeEnd()` with the same name, the browser returns the time in milliseconds since the timer was started.

#### Syntax
```js
time(label)
```
#### Use-case
These methods can be used to calculate how much time a function takes to run.
```js
console.time();
function Foo () {
//do something
};
console.timeEnd();
//=> default: 0.00... ms
```

## The `debugger` statement
The `debugger` statement activates any debugging capability available, such as setting a breakpoint. This statement has no impact if no debugging functionality is present.

#### Syntax
```js
debugger;
```
#### Use-case
The `debugger` statement can be use when you want to check the behavior of a potentially buggy function.
```js
function potentiallyBuggyFunction() {
  debugger;
  // do potentially buggy stuff to examine, step through, etc.
}
```
When the `debugger` is invoked, execution is paused at the `debugger` statement just like a breaking point.
![debugger example](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/debugger/screen_shot_2014-02-07_at_9.14.35_am.png)

## Reference
 - [Debugger's statement - Developer Mozilla Organization](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/debugger?retiredLocale=vi)
 - [Console Object - Developer Mozilla Organization](https://developer.mozilla.org/en-US/docs/Web/API/console)
 - [What is assert in JavaScript? - StackOverflow](https://stackoverflow.com/questions/15313418/what-is-assert-in-javascript)
 - [What is the difference between console.dir() and console.log()? - StackOverflow](https://stackoverflow.com/questions/11954152/whats-the-difference-between-console-dir-and-console-log)
 - [Tips and Tricks for Debugging JavaScript - James Q Quick](https://www.youtube.com/watch?v=_QtUGdaCb1c&t=701s)
