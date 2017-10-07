# __Functions in Javascript__
Notes on Javascript functions

## Three types of functions

1. Function Declaration
2. Function Expression (_preferred_)
3. Immediately Invoked Function (IIFE)
    ```javascript
    var area = (function(width, height) {
        return width * height;
    }());
    ```
## Function Shorthand
let name = () => value;
```javascript
// Functions that require the score
grades.getMinScore = (scores) => scores.sort()[0];
```
## Declaration vs Expression

The difference between the two examples below

### Function Declaration
```javascript
    function getExample() {

    };
```

### Function Expression
```javascript
    let getExample = function() {

    };
```

Function Declaration
* Standalone, cannot be nestetd
* Hoisting means they can be used by parts of your program even if they haven't been declared

### Function Expressions
* This is your go to
* Clearly shows what's happenning
* Less likely to make a coding error

# Links
1. [Declaration vs Expression](https://javascriptweblog.wordpress.com/2010/07/06/function-declarations-vs-function-expressions/)
