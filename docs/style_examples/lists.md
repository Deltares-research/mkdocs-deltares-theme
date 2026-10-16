---
icon: fontawesome/solid/list
---

# List styling 

## Markdown Lists

Markdown offers a simple way to create lists as is shown in the [Markdown list reference](https://www.markdownguide.org/basic-syntax/#lists-1).

For a more complex reference specifically designed for MkDocs, please refer to the reference in 
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/reference/lists/).

Through the [deltares.css](../../assets/stylesheets/deltares.css) stylesheet it is possible to style these lists.

The current styles defined in the deltares.css file are configured according to the Deltares design guidelines.

The entries for the List styles are can be found in the deltares.css under section:


````
 /* Deltares overrides for Lists */
 
````

### Unordered List

````Markdown title="Markdown Unordered List"
* First item
* Second item
* Third item
____- Subitem 1
____- Subitem 2
________+ Subsubitem 1
________+ Subsubitem 2
````

* First item
* Second item
* Third item
    * Subitem 1
    * Subitem 2
        * Subsubitem 1
        * Subsubitem 2

### Ordered List

````Markdown title="Markdown Ordered List"
1. First item
   
    ```Add an image.``` ![Deltares logo](./assets/favicon-16x16.png)
   
2. Second item

    ```Add a code block here to show that the list is still active.```

3. Third item
    1. Subitem 1
    2. Subitem 2
        1. Subsubitem 1
        2. Subsubitem 2
````

1. First item

    ```Add an image.``` ![Deltares logo](../../assets/favicon-16x16.png)

2. Second item 

    ```Add a code block here to show that the list is still active.```

3. Third item
    1. Subitem 1
    2. Subitem 2
        1. Subsubitem 1
        2. Subsubitem 2
                 
## HTML List

If you wish for more control over the styling of lists, then it is possible to use HTML and CSS.

The CSS entries for styling the HTML lists are defined in the same section of the deltares.css file as the Markdown lists.:

````
 /* Deltares overrides for Lists */
 
````

```` HTML title="HTML Ordered List"
<div class="md-typeset__list">
    <ol>
        <li>First item</li>
        <li>Second item</li>
        <li>Third item
            <ol class="md">
                <li>Subitem 1</li>
                <li>Subitem 2
                    <ol>
                        <li>Subsubitem 1</li>
                        <li>Subsubitem 2</li>
                    </ol>
                </li>
            </ol>
        </li>
    </ol>
</div>

````

<div class="md-typeset__list">
    <ol>
        <li>First item</li>
        <li>Second item</li>
        <li>Third item
            <ol class="md">
                <li>Subitem 1</li>
                <li>Subitem 2
                    <ol>
                        <li>Subsubitem 1</li>
                        <li>Subsubitem 2</li>
                    </ol>
                </li>
            </ol>
        </li>
    </ol>
</div>

