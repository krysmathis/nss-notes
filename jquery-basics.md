# Jquery

# Setting up jquery
Put scripts at the bottom of your page
https://code.jquery.com/

# The jquery object
$(css selector)

## Chaining
you can chain the functions one after the other

# Selecting Page Elements With Jquery

### __Element Selectors__
$('li')
$('p')

### __Descendent Selectors__
$('p a')

### __Classes and Id's__
$('.main-content')
$('#about')

### __Attribute Selectors__
$([name='newsletter'])

# Basic Example

```javascript
const $bigA = $('a');
let a = $bigA.attr('href');
console.log(a);

$('button').on('click', function () {
  $bigA.attr("href", "http://www.github.com");
  console.log($bigA.attr('href'));
});
```