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
We can avoid inheritance with, 
`initial`.

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