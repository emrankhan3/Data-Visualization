# Data-Visualization

### Add Document Elements with D3
D3 has several methods that let you add and change elements in your document.

The select() method selects one element from the document. It takes an argument for the name of the element you want and returns an HTML node for the first element in the document that matches the name. Here's an example:
```js
const anchor = d3.select("a");
```
Two other useful methods are 
**append()** and **text()**

The append() method takes an argument for the element you want to add to the document. It appends an HTML node to a selected item, and returns a handle to that node.
The text() method either sets the text of the selected node, or gets the current text. To set the value, you pass a string as an argument inside the parentheses of the method.

Here's an example that selects an unordered list, appends a list item, and adds text:
```js
d3.select("ul")
  .append("li")
  .text("Very important item");
```
D3 allows you to chain several methods together with periods to perform a number of actions in a row.
 The code below select method to select the body tag in the document. Then append an h1 tag to it, and add the text Learning D3 into the h1 element.
 ```js
  <body>
  <script>
    const anchor = d3.select("body");
    anchor.append('h1')
    .text("Learning D3")
  </script>
</body>
```
## Select a Group of Elements with D3
D3 also has the selectAll() method to select a group of elements.
It returns an array of HTML nodes for all the items in the document that match the input string.
```js
const anchors = d3.selectAll("a");
```
Like the select() method, selectAll() supports method chaining, and you can use it with other methods.

The code below select all of the li tags in the document, and change their text to the string list item by chaining the .text() method.
```js
  <body>
    <ul>
      <li>Example</li>
      <li>Example</li>
      <li>Example</li>
    </ul>
    <script>
      // Add your code below this line
      const anchor = d3.selectAll('li')
      console.log(anchor)
      anchor.text('list item')
  
  
      // Add your code above this line
    </script>
  </body>
```
## Work with Data in D3
The D3 library focuses on a data-driven approach. When you have a set of data, you can apply D3 methods to display it on the page. Data comes in many formats, but this challenge uses a simple array of numbers.

The first step is to make D3 aware of the data. The data() method is used on a selection of DOM elements to attach the data to those elements. The data set is passed as an argument to the method.

A common workflow pattern is to create a new element in the document for each piece of data in the set. D3 has the enter() method for this purpose.

When enter() is combined with the data() method, it looks at the selected elements from the page and compares them to the number of data items in the set. If there are fewer elements than data items, it creates the missing elements.

Here is an example that selects a ul element and creates a new list item based on the number of entries in the array:

<body>
  <ul></ul>
  <script>
    const dataset = ["a", "b", "c"];
    d3.select("ul").selectAll("li")
      .data(dataset)
      .enter()
      .append("li")
      .text("New item");
  </script>
</body>

It may seem confusing to select elements that don't exist yet. This code is telling D3 to first select the ul on the page. Next, select all list items, which returns an empty selection. Then the data() method reviews the dataset and runs the following code three times, once for each item in the array. The enter() method sees there are no li elements on the page, but it needs 3 (one for each piece of data in dataset). New li elements are appended to the ul and have the text New item.

Select the body node, then select all h2 elements. Have D3 create and append an h2 tag for each item in the dataset array. The text in the h2 should say New Title. Your code should use the data() and enter() methods.


<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    // Add your code below this line
  const anchor = d3.select('body')
  anchor.selectAll('h2')
  .data(dataset)
  .enter()
  .append('h2')
  .text('New Title')

    // Add your code above this line
  </script>
</body>






## Add Inline Styling to Elements
D3 lets you add inline CSS styles on dynamic elements with the style() method.

The style() method takes a comma-separated key-value pair as an argument. Here's an example to set the selection's text color to blue:

selection.style("color","blue");
Add the style() method to the code in the editor to make all the displayed text have a font-family of verdana.
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    d3.select("body").selectAll("h2")
      .data(dataset)
      .enter()
      .append("h2")
      .text((d) => (d + " USD"))
      .style('font-family','verdana')
      // Add your code below this line



      // Add your code above this line
  </script>
</body>



-----------
## Change Styles Based on Data
D3 is about visualization and presentation of data. It's likely you'll want to change the styling of elements based on the data. For example, you may want to color a data point blue if it has a value less than 20, and red otherwise. You can use a callback function in the style() method and include the conditional logic. The callback function uses the d parameter to represent the data point:

selection.style("color", (d) => {

});
The style() method is not limited to setting the color - it can be used with other CSS properties as well.

Add the style() method to the code in the editor to set the color of the h2 elements conditionally. Write the callback function so if the data value is less than 20, it returns red, otherwise it returns green.

Note: You can use if-else logic, or the ternary operator.

<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    d3.select("body").selectAll("h2")
      .data(dataset)
      .enter()
      .append("h2")
      .text((d) => (d + " USD"))
      // Add your code below this line

      .style('color',(d)=>{
        return d<20?'red':'green'
      })

      // Add your code above this line
  </script>
</body>
----------------------

## Add Classes with D3
Using a lot of inline styles on HTML elements gets hard to manage, even for smaller apps. It's easier to add a class to elements and style that class one time using CSS rules. D3 has the attr() method to add any HTML attribute to an element, including a class name.

The attr() method works the same way that style() does. It takes comma-separated values, and can use a callback function. Here's an example to add a class of container to a selection:

selection.attr("class", "container");
Note that the class parameter will remain the same whenever you need to add a class and only the container parameter will change.

Add the attr() method to the code in the editor and put a class of bar on the div elements.
<style>
  .bar {
    width: 25px;
    height: 100px;
    display: inline-block;
    background-color: blue;
  }
</style>
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    d3.select("body").selectAll("div")
      .data(dataset)
      .enter()
      .append("div")
      .attr("class", "bar")
      // Add your code below this line



      // Add your code above this line
  </script>
</body>

----------------------------
## Update the Height of an Element Dynamically
The previous challenges covered how to display data from an array and how to add CSS classes. You can combine these lessons to create a simple bar chart. There are two steps to this:

Create a div for each data point in the array

Give each div a dynamic height, using a callback function in the style() method that sets height equal to the data value

Recall the format to set a style using a callback function:

selection.style("cssProperty", (d) => d)
Add the style() method to the code in the editor to set the height property for each element. Use a callback function to return the value of the data point with the string px added to it.

<style>
  .bar {
    width: 25px;
    height: 100px;
    display: inline-block;
    background-color: blue;
  }
</style>
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    d3.select("body").selectAll("div")
      .data(dataset)
      .enter()
      .append("div")
      .attr("class", "bar")
      // Add your code below this line
      .style('height',(d)=>
        `${d}px`
  )


      // Add your code above this line
  </script>
</body>


-----------------
## Change the Presentation of a Bar Chart
The last challenge created a bar chart, but there are a couple of formatting changes that could improve it:

Add space between each bar to visually separate them, which is done by adding a margin to the CSS for the bar class

Increase the height of the bars to better show the difference in values, which is done by multiplying the value by a number to scale the height

First, add a margin of 2px to the bar class in the style tag. Next, change the callback function in the style() method so it returns a value 10 times the original data value (plus the px).

Note: Multiplying each data point by the same constant only alters the scale. It's like zooming in, and it doesn't change the meaning of the underlying data.

<style>
  .bar {
    width: 25px;
    height: 100px;
    /* Add your code below this line */
    margin: 2px;
    
    /* Add your code above this line */
    display: inline-block;
    background-color: blue;
  }
</style>
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    d3.select("body").selectAll("div")
      .data(dataset)
      .enter()
      .append("div")
      .attr("class", "bar")
      .style("height", (d) => ((d*10) + "px")) // Change this line
  </script>
</body>
---------------
## Learn About SVG in D3
SVG stands for Scalable Vector Graphics.

Here "scalable" means that, if you zoom in or out on an object, it would not appear pixelated. It scales with the display system, whether it's on a small mobile screen or a large TV monitor.

SVG is used to make common geometric shapes. Since D3 maps data into a visual representation, it uses SVG to create the shapes for the visualization. SVG shapes for a web page must go within an HTML svg tag.

CSS can be scalable when styles use relative units (such as vh, vw, or percentages), but using SVG is more flexible to build data visualizations.

Add an svg node to the body using append(). Give it a width attribute set to the provided w constant and a height attribute set to the provided h constant using the attr() or style() methods for each. You'll see it in the output because there's a background-color of pink applied to it in the style tag.

Note: When using attr() width and height attributes do not have units. This is the building block of scaling - the element will always have a 5:1 width to height ratio, no matter what the zoom level is.
