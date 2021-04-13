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
 
