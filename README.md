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

