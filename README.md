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
