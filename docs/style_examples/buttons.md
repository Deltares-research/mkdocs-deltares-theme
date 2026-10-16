---
icon: material/button-pointer
---

# Button Styling

## Markdown Buttons
Markdown does not offer a simple way to create buttons. However the [squidfunk mkdocs](https://squidfunk.github.io/mkdocs-material/reference/buttons/) project does.


Through the [deltares.css](../../assets/stylesheets/deltares.css) stylesheet it is possible to style these buttons.

The current styles defined in the deltares.css file are configured according to the Deltares design guidelines.

The entries for the Button styles are can be found in the deltares.css under section:


````
 /* Deltares overrides for Buttons */
 
````

### Simple Button

``` markdown title="Button"
[Subscribe to our newsletter](#){ .md-button }
```
[Subscribe to our newsletter](buttons.md){ .md-button }

### Icon Button

``` markdown title="Button with icon"
[:fontawesome-solid-arrow-right:](buttons.md){ .md-button }
```
[:fontawesome-solid-arrow-right:](buttons.md){ .md-button }

## HTML Buttons

If you wish for more control over the styling of buttons, then it is possible to use HTML and CSS.

Below is an example of a button with an icon and text. The button is defined in the deltares.css file under section:

````
 /* Deltares overrides for Buttons */
 
````


### Goto Button (HTML)

```` markdown title="Goto Button"
<div class="md-group__items"> 
  <div class="md-button md-group__item__button">
    <a  href="#">
        <img alt="arrow right" width="20" height="20"  src="../../assets/arrow-right.svg">
    </a>
  </div>
  <div class="md-group__item__text">
    <a href="#" >
        <h4>Goto</h4>
    </a>
  </div>
</div>
````
`
<div class="md-group__items"> 
  <div class="md-button md-group__item__button">
    <a  href="#">
        <img alt="arrow right" width="20" height="20"  src="../../assets/arrow-right.svg">
    </a>
  </div>
  <div class="md-group__item__text">
    <a href="#" >
        <h4>Goto</h4>
    </a>
  </div>
</div>