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


