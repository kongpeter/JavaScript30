# 01 JavaScript Drum Kit

> Author: © [kongpeter](github.com/kongpeter)

## Overiew
Simulate a drum page. When the user presses the *asdfghjkl* keys on the keyboard, the buttons corresponding to the letters on the page become larger and brighter, and the corresponding drum beat sounds.

[View it: Drum Kit](https://kongpeter.github.io/JavaScript30/1-Drum%20Kit/)

## Key Features

1. Keyboard event
2. Play Sound
3. Change Style


## Step by Step guide

1. Add keyboard event monitor. Add `keydown` event to Windows.
2.  Corresponding event handler.
   i. Get key code.
   ii. get `data-key`.
   iii. Handle elements. Play sound, change style.  
3. Add `transitionened` to all `div.key`
   i. Get all elements of `key`.
   ii. Add monitors.
4. Event handler with style removal.



## Some programming grammars
### ES6
``constant``: Declare a read-only constant. The value of the identifier can only be assigned once

````javascript
          var a = 1;
          var b = 2;
          //No module
          console.log("Three is" + (a + b) + "Not" + (2 * a + b)); //"Three is 3 but 4"
          //Use module
          console.log(`Three is${a + b}but${2 * a + b}`); //"Three is 3 but 4"
````


### ``forEach`` and Arrow Function

use `document.querySelector` to get a set of element snapshots that conform to the CSS selector, and the type is NodeList (this object is a dynamic query for the real-time running of the document). The `forEach` method can be used to traverse the snapshot.

```javascript
// Code from http://es6-features.org/#StatementBodies

// ES6
nums.forEach(v => {
	if (v % 5 === 0)
		fives.push(v);
})

// ES5
nums.forEach(function (v) {
	if (v % 5 === 0)
		five.push(v);
})
```


