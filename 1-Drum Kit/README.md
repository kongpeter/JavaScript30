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
2.  Corresponding event handler.\
   i. Get key code.\
   ii. get `data-key`.\
   iii. Handle elements. Play sound, change style.  
3. Add `transitionened` to all `div.key`
   i. Get all elements of `key`.\
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


## Difficulties Solutions

### How to match keyboard with page buttons?
The way of the connection is the `keycode` attribute in the `Keydown` event. The value of the `keycode` attribute is the same as that of the ASCII code (corresponding to lower case letters). At [this website](http://keycode.info/), you can view the corresponding key code by pressing the keyboard.
In the initial page we can get, an attribute `data key` has been added to the buttons `div` and audio `audio` tags to store the corresponding key code. The purpose of this is to obtain the `keycode` attribute value of the event when the keyboard event is triggered after adding a keyboard event. This is used as a clue to operate the corresponding button and audio.

````javascript
const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`;
const key = document.querySelector(`div[data-key="${e.keyCode}"]`);
````

### How to ensure that when the key is pressed and held down, the continuous drumming sound can be heard immediately?

Set the timestamp to 0 before playing the audio.

````javascript
var audio = document.getElementById("video"); 
audio.currentTime = 0;
audio.play();
````

### How to restore the page button?
Using a event called [`transitionend`](https://developer.mozilla.org/zh-CN/docs/Web/Events/transitionend), which is triggered after the CSS transition ends. We can use this event to remove the pattern after each drum effect (larger size, color change) is completed.

In this page, there are more than one style attribute of `transition` (`box shadow`, `transform`, `border color`), so you need to add a judgment statement to remove the style only once when a key event occurs.

````javascript
funciton remove(event) {
  if (event.propertyName !== 'border-left-color') return;
  this.classList.remove('playing');
  // event.target.classList.remove('playing');
}
````