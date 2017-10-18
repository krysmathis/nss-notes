# Adding a Menu Option Using jQuery
## Created: 9-30-2017 by Krys Mathis

__This project uses a few jQuery concepts that might be new to the reader:__

* The theory of least astonishment applied: getter functions return the value with no input, the setter functions take an argument.

* One thing that tangled me up here: I just jumped right in with the coding and didn't understand the organization of the website and things I could have used to set the selected property of the option. In this case, each webpage has a class selected for the option that's selected. __From a workflow perspective, perhaps it would pay off to map out the website before jumping into coding a solution.__

* Disembodied jQuery elements, such as `$('<select></select>')` or `$('<option></option>')`

* From an HTML standpoint, an option looks like this: `<option value="href" or "something else">Ipod</option>`
    * Attributes: disabled, label, selected (true or false), value
    * the value of the `<select>` is equal to the option that is marked as `selected`. [documentation from mdn](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select)

    ```javascript
    <!-- The second value will be selected initially -->
    <select name="select"> <!--Supplement an id here instead of using 'name'-->
        <option value="value1">Value 1</option> 
        <option value="value2" selected>Value 2</option>
        <option value="value3">Value 3</option>
    </select>
    ```

* `.append()` this inserts content to the end of each element in the set of matched elements. __You can add a new menu to the current menu div.__ [see doc](https://api.jquery.com/append/ "jQuery Documentation")

* `.each()` this one loops or iterates over a jQuery object and executes a function. __used with `function()`. __You might think about looping through the menu anchors and doing something with each one, like...__

```javascript
$("#menu a").each(function() {
    //...
}); 
```

* `.hasClass()` - check to see if an element has a specific class, returns true and false

* `.attr()` - get the velue of an attribute for the first element in the set of matched elements. In, `<p lang="en-us">`, lang = the attribute, en-us = the attribute value.

* `.prop()` - sets or retrieve property, the setter takes the form of `.prop(propertyName, value). [documentation](https://api.jquery.com/prop/)

* `.text()` definition is get the combined text contents of each element in the set of matched elements, including their descendants. [documentation](https://api.jquery.com/text/). An example from the jQuery documentation


```javascript
<div class="demo-container">
  <div class="demo-box">Demonstration Box</div>
  <ul>
    <li>list item 1</li>
    <li>list <strong>item</strong> 2</li>
  </ul>
</div>
```
The code `$( "div.demo-container" ).text()` would produce the following result:

Demonstration Box list item 1 list item 2

* `.val()` get the current value of the first element in the set of matched elements. __options have a value you can set to hold the href__.

* `.parent()` get the parent of the current object

Further, the solution will take advantage of css `@media` queries to hide the display of the `li` when the screen size falls below a px range, remember: __widths are in px's!!__

## ToDos
* Get a better grasp of properties in HTML

