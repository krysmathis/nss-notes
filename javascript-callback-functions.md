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


