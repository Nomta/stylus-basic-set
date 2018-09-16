# Stylus Helpers
*Basic classes and mixins for Stylus.*  

It contains three modules:
- [base](#base) - reset styles and several useful classes, such as clearfix.
- [mixins](#mixins) - frequently used mixins.
- [media](#media) - convenient shortcuts for media queries that allow you to use breakpoint variables.

All the modules are included in `main.styl` or you can include them separately from the `base` directory.

### Base
It resets the styles of the most-used tags and adds the most common classes. Some lines are commented out. Uncomment them to apply a reset or the required classes.

Classes:
- video: determines the routine aspect ratio of 16:9
- clearfix: clears the float
- ellipsis: adds an ellipsis to the single-line text when truncating 
- hidden: `display: none` for the element
- visible: `display: block` for the element
- invisible: makes the element invisible via `opacity: 0` when it is not hovered

### Mixins
Сontains the most commonly used snippets of css rules. Allows you to shorten the writing of rules by specifying the default property values.
For example: 
- `border: red` 
- `bg-image: url(image.png) center top fixed` 
- `bg-mask: rgba(white, 0.2) 0.4s 'read more'` 
- `flex-column: center center` 
- `position: fixed auto 4em 0` 
- `size: 80vw 40vh` 
- `text: center uppercase`

#### Usage 
```
/* Before */ 

    bg-image: url(image.png)    // and other background values
  

/* After */

    background: url(image.png) no-repeat   // and other background values
    background-size: cover


/* Before */ 

    bg-mask: rgba(255, 0.1)  // makes a mask over an element
                           // optional parameters: transition-duration, content
                         
/* After */

    position: relative
    &:after
      content: ''
      display: block
      height: 100%
      width: 100%
      position: absolute
      top: 0
      left: 0
      right: 0
      bottom: 0
      z-index: 2
      background: rgba(255, 255, 255, 0.1)


/* Before */ 

    border()          // optional parameters: border-width, border-style, border-color
  

/* After */

    border: 1px solid currentColor


/* Before */ 

    flex-row()        // optional parameters: justify-content, align-items
  

/* After */

    display: flex
    flex-direction: row
    justify-content: space-between
    align-items: stretch
  

/* Before */ 

    flex-column()        // optional parameters: justify-content, align-items
  

/* After */

    display: flex
    flex-direction: column
    justify-content: flex-start
    align-items: stretch
  

/* Before */ 

    font-size: 16px / 1.6    // combines properties font-size and line-height


/* After */

    font-size: 16px
    line-height: 1.6


/* Before */ 

    outline()          // optional parameters: outline-width, outline-style, outline-color
  

/* After */

    outline: 1px solid currentColor


/* Before */ 

    position: absolute 0 0    // combines properties position and optional top, left, right, bottom (in this order) 


/* After */

    position: absolute
    top: 0
    left: 0


/* Before */ 

    size: 100%          //  combines properties width and height


/* After */

    width: 100%
    height: 100%


/* Before */ 

    text: center          // optional parameters: text-transform, color


/* After */

    text-align: center

```

*[back to top](#stylus-helpers)*  

### Media
Allows you to shorten the writing of media queries. Can be used for the `width`, `height` and `orientation` parameters of viewport.

#### Usage

```
/* Before */ 

  +media-width(1024px)


/* After */

  @media only screen and (min-width: 1024px) 


/* Before */ 

  +media-width(0, 1024px)


/* After */

  @media only screen and (max-width: 1023px) 



/* Before */ 

  +media-width(768px, 1024px)


/* After */

  @media only screen and (min-width: 768px) and (max-width: 1023px) 
  
```

Media queries for the viewport height are determined in a similar manner, e.g.:

```
/* Before */ 

  +media-height(0, 768px)


/* After */

  @media only screen and (max-height: 767px) 

```

Note: all the maximum values are reduced by one unit.   

Media queries for the device orientation:

```

/* Before */

  +media-landscape()


/* After */

  @media screen and (orientation: landscape)


/* Before */ 

  +media-portrait()


/* After */

  @media screen and (orientation: portrait)

```

You can add a device orientation parameter to a common query:

```
/* Before */ 

  +media-width(1024px, landscape)


/* After */

  @media only screen and (min-width: 1024px) and (orientation: landscape) 
  
  
/* Before */ 

  +media-height(768px, 1024px, portrait)


/* After */

  @media only screen and (min-height: 768px) and (max-height: 1023px) and (orientation: portrait) 

```

Alias for a width of a viewport:

```

/* Before */ 

  +media(0, 1024px)


/* After */

  @media only screen and (max-width: 1023px) 

```

You can use nested queries for more complex cases and variables in place of or in common with usual css units, e.g.:

```
 +media(breakpoints.small)
   +media-height(0, breakpoints.large, portrait)
 
```

*[back to top](#stylus-helpers)*  

### License
This project is available under the [MIT](./license) license.  