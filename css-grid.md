# CSS Grid System
Notes on setting up and using a grid system


# Containers and Items
### Containers
Establish the grid inside a container or wrapper
```css
.wrapper {
    display: grid;
}
```

### Items
Direct children of the container. These are the elements you will manipulate with the grid

# Definining Grid
```css
grid-template-columns: 1fr 1fr;
```
```css
grid-template-rows: 1fr minmax(200px, 1fr);
```

# Grid-Gap
You can set the gap between the grid boxes by adjusting the grid gap
```grid-gap: 20px 40px;``` or ```grid-gap: 20px;```

# Repeat Function
```repeat(3, 1fr)``` = ```1fr 1fr 1fr```

# Min Max Function
Sets the min and max height or width of the grid column or row
```css
grid-template-columns: 1fr minmax(200px, 400px) 1fr;
```

# Overflow
* ```auto-fill``` need more info
* ```auto-fit``` need more info

# Explicit and Implicit Grid
Implicit sizes the grid based on contents

## Controlling Explicit Grid
-----
With the ```grid-auto-rows``` and ```grid-auto-columns```properties you can define the size of auto generated rows

With ```grid-auto-flow: columns;``` you can define that new content is placed in columns instead of the default rows

# Position Items by Grid Lines

```css
.element {
    grid-column-start: 3;
    grid-column-end: 4; /* or -1 to extend to end */
}

.element {
    grid-column-start: 3;
    grid-column-end: span 4; /* or -1 to extend to end */
}

/* shorthand */
.element {
    grid-column: 3 / 4;
    grid-row: 1 / -1;
}
```

# Grid Order
When the grid is generated automatically you can control the order
```css 
.poison {
    order: 1;
}
```

# Grid Template Areas
### An alternate approach because what I outline below doesn't seem to work some of the times

1. Define a ```grid-template:``` in your containter
1. Define the ```grid-column``` and ```grid-rows``` in your 


1. Define ```grid-area``` for each grid item 
1. set up you ```grid-template-area``` in your grid container

```css
.container {
    grid-template-area: 
        "header"
        "main"
        "footer";

    /* extended example 
    grid-template-area:
        "header header"
        "main aside"
        "footer aside"
    */
}

header {
    grid-area: header;
}

main {
    grid-area: main;
}

footer {
    grid-area: footer;
}

```

# Media Queries
Adjust the containers with media queries