---
icon: material/table
---

# Table styling 

## Markdown Tables
Markdown offers a simple way to create tables as is shown in the [Markdown table reference](https://www.markdownguide.org/extended-syntax/#tables).
More elaborate Table styling options specifically for MkDocs can be found in the [squidfunk mkdocs](https://squidfunk.github.io/mkdocs-material/reference/data-tables/) project.

Through the [deltares.css](../../assets/stylesheets/deltares.css) stylesheet it is possible to style these tables.

The current styles defined in the deltares.css file are configured according to the Deltares design guidelines.

The entries for the Table styles are can be found in the deltares.css under section:


````
 /* Deltares overrides for Tables */
 
````

````Markdown title="Markdown Table"
| Chart Title      | Euro x1000|Index|
| :----------------| --------: |----:|
| Item 1           | XXX       |XXX  |
| Item 2           | XXX       | XXX |
| Item 3           | XXX       | XXX |
````

| Chart Title      | Euro x1000                            |Index|
| :-----------     | ------------------------------------: |-----:|
| Item 1           | XXX  |XXX |
| Item 2           | XXX | XXX |
| Item 3           | XXX | XXX |


## HTML Tables

If you wish for more control over the styling of tables, then it is possible to use HTML and CSS.

Deltares supports two colour schemes for tables: <span style="background-color: #ffffff;color:#141e95">Blue </span> 
(class="md-typeset__table__blue") and <span style="background-color: #ffffff;color:#00e399">Green</span> (class="md-typeset__table__green").

The definitions for these table styles are defined in the deltares.css file under section:

````
 /* Deltares overrides for Tables */
 
````


=== "Blue"

    ````Html title="HTML Table definition"
        <table class="md-typeset__table__blue">
            <tr >
              <th align="left">Chart Title</th>
              <th align="right">Euro x1000</th>
              <th align="right">Index</th>
            </tr>
            <tr >
              <td align="left">Item 1</td>
              <td align="right">XXX</td>
              <td align="right">XXX</td>
            </tr>
            <tr >
              <td align="left">Item 2</td>
              <td align="right">XXX</td>
              <td align="right">XXX</td>
            </tr>
            <tr >
              <td align="left"><strong>Item 3</strong></td>
              <td align="right"><strong>XXX</strong></td>
              <td align="right"><strong>XXX</strong></td>
            </tr>
        </table>
    ````

    <table class="md-typeset__table__blue">
        <tr >
          <th align="left">Chart Title</th>
          <th align="right">Euro x1000</th>
          <th align="right">Index</th>
        </tr>
        <tr >
          <td align="left">Item 1</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
        <tr >
          <td align="left">Item 2</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
        <tr >
          <td align="left"><strong>Item 3</strong></td>
          <td align="right"><strong>XXX</strong></td>
          <td align="right"><strong>XXX</strong></td>
        </tr>
    </table>

    <br />

    ````Html title="HTML Table definition"
        <table class="md-typeset__table__blue">
        <tr >
          <th align="left">Chart Title</th>
          <td align="right">Item 1</td>
          <td align="right">Item 2</td>
          <td align="right">Item 3</td>
        </tr>
        <tr >
          <th align="left">Euro x1000</th>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
        <tr >
          <th align="left">Index</th>          
          <td align="right">XXX</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
    </table>
    ````
    
    <table class="md-typeset__table__blue">
        <tr >
          <th align="left">Chart Title</th>
          <td align="right">Item 1</td>
          <td align="right">Item 2</td>
          <td align="right">Item 3</td>
        </tr>
        <tr >
          <th align="left">Euro x1000</th>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
        <tr >
          <th align="left">Index</th>          
          <td align="right">XXX</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
    </table>

=== "Green"

    <table class="md-typeset__table__green">
        <tr >
          <th align="left">Chart Title</th>
          <th align="right">Euro x1000</th>
          <th align="right">Index</th>
        </tr>
        <tr >
          <td align="left">Item 1</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
        <tr >
          <td align="left">Item 2</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
        <tr >
          <td align="left"><strong>Item 3</strong></td>
          <td align="right"><strong>XXX</strong></td>
          <td align="right"><strong>XXX</strong></td>
        </tr>
    </table>

    <br />

    <table class="md-typeset__table__green">
        <tr >
          <th align="left">Chart Title</th>
          <td align="right">Item 1</td>
          <td align="right">Item 2</td>
          <td align="right">Item 3</td>
        </tr>
        <tr >
          <th align="left">Euro x1000</th>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
        <tr >
          <th align="left">Index</th>          
          <td align="right">XXX</td>
          <td align="right">XXX</td>
          <td align="right">XXX</td>
        </tr>
    </table>
