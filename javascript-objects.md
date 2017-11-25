# Javascript Objects
* You can use Quokka in VS Code to live code javascript

## Important Properties
* a way to represent a physical thing in code, it has properties
* unlike c# there are no classes (object factories)
* __.hasOwnProperty("x")__ -> returns true and false depending of whether the object has that property

## The basic way to define an object
const human = {
    "species": "human",
    saySpecies: function() {
        console.log(this.species);
    },
    sayName: function() {
        console.log(this.name);
    }
};

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

```

## Defining Getters and Setters

```javascript
const newObj = function() {
    
    let _val = 5;
    
    // Object.create is a function!!!
    return Object.create(null,{
        "foo": {
            writable: true,
            configurable: true,
            value: "hello"
        },
        "v": {
            value: 5,
            enumerable: true,
            writable: true
        },
        "hiddenValue": {
            get: function() {return _val;},
            set: function(v) {_val = v;}
        }
    });
};


const obj = newObj();
console.log(obj.hiddenValue.get()); //returns 5
obj.hiddenValue.set(20);
console.log(obj.hiddenValue.get()); //return 20
```

## Composition Using Object.assign

```javascript
// The composed object
const obj = (name) => {
    
    let state = {
        "musicType": "heavy",
        "volume": "loud"
    };

    return Object.assign({}, 
        clapper(state)
    );
};

// it is made up of smaller objects
const clapper = function(state) {
    return Object.create(null,{
        happy: {
            value: false,
            enumerable: true,
            writable: true
        },
        applaud: 
        {
            value: function() { console.log("clap,clap,clap")},
            enumerable: true, // has to be enumerable for this to work!
            writable: true
        },
    });
};
// const clappy = clapper("one");
// clappy.applaud();

const obie = obj("obie");
obie.applaud();

// obie has access to the properties of it's composed objects
console.log(obie.happy);
obie.happy = true;
console.log(obie.happy);

// the original clapper object has it's own state
const clappy = clapper();
console.log(clappy.happy);
clappy.applaud();
```