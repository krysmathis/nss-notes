# Javascript Objects
* You can use Quokka in VS Code to live code javascript

## Important Properties
* a way to represent a physical thing in code, it has properties
* __.hasOwnProperty("x")__ -> returns true and false depending of whether the object has that property

## Prototypal Inheritance vs Classical

### Classical

```javascript
function Person() {

}

var will = new Person();
```
### Prototypical

```javascript
var human = {
    "species": "human",
    saySpecies: function() {
        console.log(this.species);
    },
    sayName: function() {
        console.log(this.name);
    }
};

// Now create an object that inherits the human properties
var musician = Object.create(human);
musician.playInstrument = function() {
    console.log("plays..." + this.instrument);
};

var will = Object.create(musician);
will.name = "Will";
will.instrument = "Drums";

