# Javascript Callback Functions
Asynchronous Programming

## What is a callback?
A function that's passed into another function and gets executed at a future time, or when an event like a user-interruption occurs.

### No parentheses?
You wouldn't use parentheses with a variable. A callback is the same thing a function passed as a variable.

> In the example below the 'callbackFunction' is the callback function

```javascript
function callbackFunction() {
    // Do something
}

function exeuteCallback("text", callback) {
    // Do something
}

executeCallback("someText", callbackFunction); //notice no parentheses
```
another simple one

```javascript
function sayHello() {
    console.log("hello");
}

function executeCallback( callback ) {
    callback();
}

executeCallback(sayHello);
```
## Anonymous Functions
Also known as in-lining or writing a function inline. These are often seen as more explicit

How you could change the example above:
```javascript

function executeCallback( callback ) {
    callback();
}

executeCallback(function(){
    console.log("hello");
});
```

## Arrow Functions
Fat arrows to simplify

```javascript
function executeCallback(callback) {
    callback();
}

executeCallback(() => console.log("hello"));

executeCallback(() => console.log('goodbye'));
```
## Using Timers

### setTimeout (one-time)
```setTimeout(callback, delay)```

```javascript
const surpriseSection = document.getElementById('surprise');

let randomTime = Math.random() * 4000;

setTimeout(() => 
    surpriseSection.textContent = '🎉 Surprise! 🎉', randomTime);
```

### setInterval
```javascript
setInterval(callback,interval);
```
Updating a clock page: [jsfiddle](https://jsfiddle.net/zosgamwh/)

! The callback doesn't launch immediately, you'll need to call it yourself if you want it to launch right away.

## Callback Functions with Arguments

```javascript
const div1 = document.getElementById('first');

function makeRed(element) {
    element.style.backgroundColor = "red";
}

function addStyleToElement(element,callback) {
    callback(element);
}

addStyleToElement(div1, makeRed);
           
```

# Callbacks and the DOM

## Using the same callback on multiple objects
```javascript
element.addEventListener(eventType, callback);
```

Events are triggered when a matching eventType is executed. Events have two properties.
```
event.type
event.target
```
__Remember that the addEventListener will pass in the event object__. You can use the two properties of type and target to make changes.

Example
```javascript
const nameInput = document.getElementById('name');
const messageTextArea = document.getElementById('message');

const focusHandler = event => {
  event.target.className = "highlight";
};

const blurHandler = event => {
  event.target.className = "";
};

nameInput.addEventListener("focus", focusHandler);
nameInput.addEventListener("blur", blurHandler);

messageTextArea.addEventListener("focus", focusHandler);
messageTextArea.addEventListener("blur", blurHandler);
```
[example - jsfiddle](https://jsfiddle.net/k8zgqe61/);
