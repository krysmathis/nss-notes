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

