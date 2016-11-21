## jQuery and the Document Object Model (DOM)

### Learning Objectives 
- [ ] Diagram the DOM
- [ ] After selecting a DOM node, reach another node using traversal
- [ ] Reference jQuery documentation when learning a new technique
- [ ] Get data from the DOM using jQuery
- [ ] Put data into the DOM using jQuery

#### What is the DOM?
- The Document Object Model describes the structure of our content 
- The DOM structures our content like a tree:
- ![Image DOM Tree](http://www.w3schools.com/js/pic_htmltree.gif)
- It is our **programming interface** for html, allowing programmers to write code that manipulates our content.
- It is not a part of javascript or jQuery, but usually accessed using javascript

#### How do we access the DOM?
- In the Chrome console (Cmd + Option + j), type `document`
- Explore this object: `document.head`, `document.body`, what else is available via the `document` object?
- Javascript allows us to query and manipulate elements in the DOM. We can do things like...
 - Add new elements
 - Change text of elements
 - Add event handlers to elements (`onclick`, [`onmousedown`](http://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_onmousedown_html), `onkeypress`, etc) (more on this next lesson...)
 
#### Code Together
- Create a blank index.html page
- Using Javascript, append a new element, an H1 tag, to the top of the index.html page
- Change the text of the H1 tag

#### You Try:
- Using Javascript, add a `<div>` with a `<button>` inside of it, with any text you want inside the button
- Put this javascript into a separate JS file

### What is jQuery?
- "write less, do more" javascript library
- syntactic sugar for javascript - people often confuse javascript and jQuery ("do you know how to program with jQuery?” will really make some people cringe!)
- created by John Resig in 2006
- most associated with dom tree traversal, putting data into and getting data from the dom, ajax, event handling and animation
- a website can have a 'jQuery look and feel' - uses lots of jquery default animations and jquery-ui library elements
- How to install and use a JS library? 
  - Download and include a local library, or link to a library on the web. Both reference the location in `<script>` tags
  - [jQuery website](https://jquery.com/)
  - Take a few minutes and add jQuery to your index.html page. How do you know it's loaded?
  
### jQuery Selectors
- Uses "selectors" (just like CSS), to target elements. 
  - Returns elements in a jQuery object which looks like an array, but has jQuery methods available to it.
  - jQuery() — which can also be written as $() — searches through the DOM for any elements that match the provided selector and creates a new jQuery object that references these elements:
  - What does `$( "div.foo" );` do?
  - If no elements match the provided selector, the new jQuery object is "empty"; that is, it contains no elements and has `.length` property of 0.

#### Code Together: Selecting elements and adding styles
Find all p elements that are children of a div element and apply a border to them.

```
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery demo</title>
  <script src="https://code.jquery.com/jquery-1.10.2.js"></script>
</head>
<body>
 
<p>one</p>
<div><p>two</p></div>
<p>three</p>
 
<script>

</script>
 
</body>
</html>
```
<details><summary>Answer:</summary>
<p>

<code>$( "div > p" ).css( "border", "1px solid gray" );</code>
</p>
</details>

### Discussion: What is $(document).ready()?
```
 // A $( document ).ready() block.
$( document ).ready(function() {
    console.log( "ready!" );
});
```
- shortcut: $(function(){}

### DOM Tree-Traversal using jQuery
- how to go up, down and sideways??
- Give wireframe
- Diagram
- Traverse

#### DOM Manipulation using jQuery


#### Tie it all together:
- create a button on your html page with a class of 'continue' and some text inside the button...

<details><summary>Get the `button` element with class `continue` and change it's text to "Next Step..."</summary>
<p>
```
$( "button.continue" ).html( "Next Step..." )
```
</p>
</details>


### Discussion: Why use jQuery over directly working with a DOM object?
- reference: [learn.jquery.com](https://learn.jquery.com/using-jquery-core/jquery-object/)

### Discussion: What happens if you get a javascript library conflict?
- reference: [learn.jquery.com](http://learn.jquery.com/using-jquery-core/avoid-conflicts-other-libraries/)

#### Vocab
<details><summary>programming interface: </summary>
<p>Allows programmers to write code to interact (send and receive messages) with the instance of the class (or object).</p>
</details>
<details><summary>DOM:</summary>
<p>Document Object Model</p>
</details>
<details><summary>tree traversal:</summary>
<p></p>
</details>
<details><summary>jQuery:</summary>
<p></p>
</details>
