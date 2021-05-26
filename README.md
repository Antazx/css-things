# CSS 

## How to link CSS with HTML (4 ways)
- On css folder: /css/styles.css (**Best way**)

    ```
    <link rel="stylesheet" href="css/styles.css">
    ```
- With the style tag on HTML head (Maintenance problems)
    ```
    <head>

    ...

    <!-- Best way -->
    <link rel="stylesheet" href="css/styles.css">

    <style>
        body {
            background-color: beige;
        }
    </style>
    </head>
    ```
    This option is used to aply styles to emails with css and other strange exceptions
- CSS in line (Deprectated, **Bad practice**)
    ```
    <h1 style="background-color: yellow;">How to link CSS with HTML pages</h1>
    ```
- Import css file to style file (**Bad user experience**)
    ```
    <style>
        @import url(css/styles.css)
    </style>
    ```
    Don't use this method, it will load the css asynchronously, bad user experience, the html loads and after the css

## CSS Syntax
- Selector: element to which we are going to apply styles
- Property: what we are going to change
- Value: new value
- Decalaration: Property:value
- Rule: Selector + decaration(s)

    ```
    selector {
        property: value; 
        property2: value;
        ...
        properyN: value;
    }
    ```

## Selector types
- Simple selector:

    - Elemental selectors:
        - Universal selector: `* {...}`
        - Tag/Type selector: `body {...}`

    - Atributte selectors:
        - ID selector: `#id {...}` **case sensitive** not recomended, we want to be able to reuse styles
        - Class selector: `.class {...}` the good ones
        - Other atributtes:
        
            ```
            [href] {...}

            [atributte = "value"] {...} atributte equal to

            [atributte ^= "value"] {...} atributte starts with

            [atributte *= "value"] {...} atributte contains

            [atributte $= "value"] {...} atributte ends with

            [atributte |= "value"] {...} atributte starts with value-*
            ```

- Composed selectors:
    - Grouped selectors:
        ```
        .class,
        .class-1,
        .class-2 {...}
        ```
    - Combinatorial selectors:
        - Descendant selector:
            ```
            div .class {...}
            ```
            Not use depth < 2 levels, perfomance problems
        - Next brother element selector:
            ```
            h4 + p {...}
            ```
        - All brothers element selector:
            ```
            h4 ~ p {...}
            ```
        - Direct childs
            ```
            div > p {...}
            ```
    - Pseudoclassess & pseudoelements
## Specifity & cascade
- Speciffity: sets how specific a selector is to know which style to apply, the browser calculates the specifity and the style of the selector with the highest value is applied, it's calculated in the following way:

    | Selector                              | Specifity value   |
    | ------------------------------------- | :---------------: |
    | Tags and pseudoelements               | 001               |
    | Classess, atributtes y pseudoclassess | 010               |
    | Ids                                   | 100               |
    | Line styles                           | 1000              |

    So tag + class + id = 001 + 010 + 100 = 111
    !important overwrites all specifities **Dont use, bad practice**
    [Check specifity graph](https://jonassebastianohlsson.com/specificity-graph/)

    When there are two or more selectors with the same specifity, cascade is applied, the last selector will be applied

## Inheritance
Some parent properties are applied to their childs:

```
<h1 id="title" class="title">Fundamentos de <span>CSS</span></h1>
```

span tag gets some styles from h1 tag. If not everything will be a chaos
Inherited properties:
- color properties
- font properties

Links `<a></a>` wont inherit any property, we can force inheritance with `inherit`.

We can avoid inheritance with, `initial`

## Web development tools (F12)
Elements -> HTML
Styles from browser = user agent stylesheet
Our styles = *.css
Computed -> Properties applied to selected element and how them were calculated. WWe can also navigate to the source in the css file.

## [Normalice CSS](https://necolas.github.io/normalize.css/)
We can reset the default browser styles to display the same in all the browsers. We can download the [normalice.css](https://necolas.github.io/normalize.css/) and link it to the HTML **before** our stylesheet:

    ```
    <link rel="stylesheet" href="css/normalice.css">
    <link rel="stylesheet" href="css/styles.css">
    ```

## Property prefixes
We need to add some prefixes to the properties so that they can be interpreted correctly by browsers. We can use the [Autoprefixer tool](https://autoprefixer.github.io/) to solve this problem.

## Box model
Each html element is rendered as a box composed by:

- content
- padding: distance from the content to the border
- border: border of the box
- margin: distance from the border to the next element
- heigth: vertical size
- width: horizontal size
    
We can change how the total size of the elements is calculated with box-sizing 

## Heigth & Width
The behaviour is different for block and line elements:

- block elements: defined with the properties heigth and width
- line elements: **inline elements haven't heidth or width, its size is determined by its content**

## Margin
This property margin allows us to generate space between elements, it's a shorcut for the 4 sides:

- margin-top
- margin-right
- margin-bottom
- margin-left

It supports up to four values on clock direction:

- 4 values: top, right, bottom, left 
- 3 values: top, right-left, bottom
- 2 values: top-bottom, left-right
- 1 values: all sides the same

The behaviour is different for block and line elements:

- block elements: defined with the properties heigth and width
- line elements: **inline elements onnly have rigth and left margins**

If we set margin to auto, it takes all the available space

- Common errors:
    
    ```
    * {
        margin: 0;
        padding: 0;
    }
    ```
    It disables all the paddings and elements and it's necessary to reset all of them one by one.
    ```
    .block {
        margin-top: 100px;
        margin: 0 auto;

        /* one way to solve it */
        /* the element it's centered without loosing top value */
        margin-top: 100px;
        margin-left: auto;
        margin-right: auto;
    }
    ```
    margin it's overwitting the margin-top value.

**By default the body element has a 8px margin** so it's not bad to set body {margin: 0;}
We can avoid inheritance with, `initial`

## Padding
It is the property that allows us to generate internal space between the border and the box. It is a shorthand property that controls the 4 possible sides to give padding to:

- padding-top
- padding-right
- padding-bottom
- padding-left

Supports up to 4 values in clockwise order: 

- 4 values: top, right, bottm, left 
- 3 values: top, right/left, bottom
- 2 values: top/bottom, left/right
- 1 values: top/right/bottom/left

Use padding to increase the size of our element, not to move it away from other elements.

## Border
It is the property that allows us to modify the element's border. Its a shorthand property that grop this other three:

- border-width
- border-style: none, hidden, dotted, dashed, solid, double, groove, ridge, inset, outset
- border-color
- border: 10px solid red;

All those properties are also shorthands:

- border-width:
    - border-top-width
    - border-right-width
    - border-bottom-width
    - border-left-width
- border-style:
    - border-top-style
    - border-right-style
    - border-bottom-style
    - border-left-style
- border-color:
    - border-top-color
    - border-right-color
    - border-bottom-color
    - border-left-color

## Box sizing:
This is the property that allows us to control the calculation made by the browser when modifying the content, padding and border properties. It has two values:

- content-box: default value, size = content 
- border-box: takes padding and border into account

    ```
        .box-model {
            width: 400px;
            height: 400px;

            margin-left: auto;
            margin-right: auto;

            padding: 20px;
            border: 5px solid black;
        }
    ```

With content-box:
- height: content: 400px + padding: 40px + 40px + border: 5px + 5px = 450px 
- width: content: 400px + padding: 40px + 40px + border: 5px + 5px = 450px 

With border-box:
- height = 400px = content + padding + border
- width = 400px = content + padding + border

To set the same box-sizing for all the elements:

```
* {
    box-sizing: border-box;
}
```

## Border radius:
This property allows us to round the vertices, it's a shorthand for four properties:

- border-top-left-radius
- border-top-rigth-radius
- border-bottom-left-radius
- border-bottom-rigth-radius

With one value it will draw a circle on each vert and supports up to four values:

- 1 values: top-left/top-rigth/bottom-right/bottom-left
- 2 values: top-left/bottom-right, top-right/bottom-left
- 3 values: top-left, top-right/bottom-left, bottom-right
- 4 values: top-left, top-right, bottom-right, bottom-left

With two values it will draw an elipse instead of a circle:
```
- border-top-left-radius: 50px 100px
```
It will draw an elipse with 50px on X radius and 100px on Y radius, when using with the sorthand its a strange sintaxis:

- border-radius: 50px 100px 150px 200px/ 100px 50px 150px 200px;
    - border-top-left-radius: 50px 100px
    - border-top-rigth-radius: 100px 50px
    - border-bottom-left-radius: 150px 150px
    - border-bottom-rigth-radius: 200px 200px

## Overflow
The content overflows then the container is smaller than the content, this property controls the behaviour of the container when it's content overflows. It's also a shorthand of two properties:
- overflow-x
- overflow-y

It has for values: 
- visible: default value
- hidden: the content that overflows will not be seen, if we apply this property to one axis the other will set with scroll
- scroll: the scroll bars appear on the assigned axis
- auto: scrollbars appear only when necessary

When we have a container with border radius and its content overflows on the verts, we need to center the content and set `overflow: hidden` to round the content on the container verts

## Margin collapse
There is a problem with css, if we have two boxes one on top of the other, the first one with a `margin-bottom: 20px` and the second one with a `margin-top 20px`, the distance between them will not be 40px, but 20px. This is because the vertical margins collapse. There is no solution, the recomedation is to set only margin-bottom to avoid this behaviour. This only happens on vertical margins. There are another problem with vertical margins, when a child has a vertical margin it will be applied to the parent, we can solve it with:

```
.container {
    //Hack 1
    overflow: hidden;

    //Hack 2, it creates space between the margin of the parent and the content of the child
    padding-top: 0.1;

    //Hack 3, it also creates space between ...
    border-top: 0.1 solid red;
}
```

## Display
The display property is used to change the context of the elements within the browser.
It admits several values:
- none: makes the element not to be displayed, but it is still loaded.
- block: makes the element a block element
- inline: makes the element a line element.
- inline-block: makes the element inline but allows vertical dimensions and margins. When we have an element that is a line element but we need it to be a line element but we have to give it measures or vertical margins.

## Outline
Outline is the property that allows us to draw a border outside the box model. It is a shorthand containing:
- outline-width: controls the width of the outline
- outline-style: controls the outline style
- outline-color: controls the colour of the outline

It has the same properties and syntax as border, but with some differences.
It does not occupy space, as it is not part of the box-model.
You cannot control the sides independently.

It also has the outline-offset property, which allows you to increase or decrease the distance of the outline in relation to the box it belongs to.

## Text align
Text-align is the property that allows us to align the content of a block element horizontally as long as **the content does not have a delimited width**.

- text-align: left; aligns content to the left
- text-align: right; align content to the right
- text-align: centre; aligns the content in the middle
- text-align: justify; aligns the content justified. Not recommended

**Centres the content, not the container**
## Box shadow
The box-shadow property was created to add shadow effects to our box. What it does is to create a duplicate of the box respecting the shape of its box-model (width, height, roundness).

The syntax of box-shadow can be written in different ways, depending on our objective, we can give it the following values:
- offset-x: offset in x. Mandatory
- offset-y: offset in y. Mandatory
- blur-radius: blur of the shadow
- spread-radius: shadow expansion
- colour: colour of the shadow, if not specified it will inherit the colour of the element it belongs to.
- inset: determines if the shadow will be inner or outer

## Position
The position property allows us to position the elements. There are some concepts we need to understand:

- **Rendered flow**: As a general rule, elements are drawn from left to right and from top to bottom. The 0,0 point of the elements, as a general rule, is the upper left corner.
- **Reserved space**: This is the space that an element is assigned in the browser.
- **Positioned element**: This means that the element has the position property with a value other than "static", which is the default value for this property.
- **Staking context**: Stacking context. This is the order in which overlapping boxes will be stacked in the same container.

When positioning an element, 5 properties are enabled that we can use to move the elements in the 3 axes:

- top: the element will move from the top the distance we have indicated.
- right: the element will move from the right side the distance we have indicated.
- bottom: the element will move from the bottom the distance we have indicated.
- left: the element will move from the left side the distance we have indicated.
- z-index: allows you to move the element in the stacking context (z-axis).

**NOTE: If we declare the top and/or left property for an element, the bottom and/or right properties will not work**

The possible values that position can has are:
- static: This is the default value, with this value the element is not positioned and therefore we cannot move it.
- relative: The element will maintain its position, measurements in the rendering flow and its reserved space. If we move it, it will do using its position in the html as a reference point.
- absolute: The element will lose its measurements and its reserved space. If we move it, it will use the parent element **positioned** with reference. If they have none, it will use that of the referenced html element.
- fixed: The element will lose its measurements and its reserved space. If we move it, it will use the reference html element and it will remain fixed in that position even if we scroll.
- Sticky: is a mix of position relative and fixed. With this type of positioning the values top, left, bottom and right are not used to move the element, but to indicate at what point it will have a fixed positioning behaviour, until that point it will behave as if it had relative. It will count as positioned if we have to position other element based on it. Does not work with **overflow: !visible**

## Z-index
When two elements overlap we can choose which element is on top of the other. The one with the higher value will be on top of the other. It is not a good idea to use consecutive numbers (1, 2, 3, ...), if we have to put an element between 1 and 2 we could not. It is better to use 100, 200, 300, ... so if we have to add another element in between we can give it value 101 102 ...

For parent-child elements when we want the parent to be above the child, we have to put the child below the parent, with a negative z-index value, if we give z-index to the parent this will stop working.

If two elements have the same z-index value, who is above the other will be determined by the order of appearance in the html, the last one will be the one that is higher.
