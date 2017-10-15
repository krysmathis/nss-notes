# Working With Data
* What array calculations are there in javascript
* What does the array forEach do?

#### Code Example

```javascript
// here are database is defined as an object
const RainfallDatabase = {
    "1948" : [3.4, 3.8, 4.0, 3.9, 3.5, 3.6, 3.6],
    "1949" : [4.3, 4.7, 5.0, 5.3, 6.1, 6.2, 6.7],
    "1950" : [6.5, 6.4, 6.3, 5.8, 5.5, 5.4, 5.0],
    "1951" : [3.7, 3.4, 3.4, 3.1, 3.0, 3.2, 3.1],
    "1952" : [5.8, 6.4, 6.7, 7.4, 7.4, 7.3, 7.5]
  }

  //What is the total rainfall per year
  // A holder for our objects
  const yearlyTotal = [];

  // To loop through an object use the for..in loop
  for (let key in RainfallDatabase){
      // you have to use the bracket notation to get the value of the propery
      let currentYear = RainfallDatabase[key];
      // variable to hold the total
      let totalRainfall = 0;

      // Looping through current year array
      for (let month = 0; month < currentYear.length; month++) {
            totalRainfall += currentYear[month];
      }
      // Now add a new object with year and rainfall total to the array
      yearlyTotal.push({"year": key, "rainfall": totalRainfall});
      
  }
  yearlyTotal

```


## Array Methods
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
### Array methods require a function
* map
* filter
* reduce
* forEach

```javascript
let findValue = "1950";
yearlyTotal.find(function(yearObject){
    if (yearObject.year === findValue) {
        console.log(yearObject.rainfall)
    }
});
```
## Local Data

```javascript
localStorage.setItem()
localStorage.getItem()

//elephant example that doesn't work...because its not serialized
localStorage.setItem("elephant", elephant)
localStorage.getItem("elephant") //--returns "[object Object]"
```
You need to "serialize" data, JSON is a method to do this

```javascript
localStorage.setItem("rainfall",JSON.stringify(RainfallDatabase));
JSON.parse(localStorage.getItem("rainfall"));
```
### a way to sort an array of objects
```javascript
const sortedGrades = [{A:4}, {B:3}, {C:5}];

let finalResults = sortedGrades.sort(function(first, second) {
    const firstNumberOfGrades = Object.values(first)[0]
    const secondNumberOfGrades = Object.values(second)[0]
    return secondNumberOfGrades - firstNumberOfGrades
});

finalResults
```

### Challenges
- [ ] Challenge use the forEach loop on an array
- [x] another to do item

