# CSS
[code pen](https://codepen.io/pen/)


## The rules
1. The last one always wins


### Descendent selectors
">" - direct descendants only

Selecting div that fall within a div that is a child of another div
```css
/* Make the "I'm red" text colored red. */
.parent div > div {
    color: red;
}
```
Here select the second div because it is a sibling
```css
/* Make the "I'm blue" text colored blue. */
.parent div ~ div {
    color: blue;
}

```
