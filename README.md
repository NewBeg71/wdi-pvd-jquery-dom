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
 - Add new elements:
   - `document.createElement('elementName')`
 - Move elements around:
   - `document.body.appendChild('elementName')`
 - Change text of elements:
   - `document.getElementsByTagName('a')[0].innerHTML('some new text')`
   - why did we need to use `[0]`?
 - Add event handlers to elements (`onclick`, [`onmousedown`](http://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_onmousedown_html), `onkeypress`, etc) (more on this next lesson...)
 
#### Code Together
- Create a blank index.html page. Save this page to disk and load it in Chrome. Open the Chrome console to work with this page.
- Using Javascript, create a new `h1` element. Append this new element to the top of the page, directly under the opening `<body>` tag.
- Change the text of your `h1` tag
- Add an attribute, id, to the `h1` tag
  - reference: [setAttribute](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute)

#### You Try:
- Using Javascript in the Chrome Console, create a `<div>` element. Within the `<div>`, **append** a `<button>` element inside of it. Append below your `h1` tag.  Put any text you want inside the button.
- Give the button a class name of "pvd"
- Write this javascript to a separate javascript file, and load the file into your index.html page. The javascript should execute at page load. When would you not want the javascript to execute on page load?

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

### DOM Tree-Traversal using jQuery
- Draw wireframe
- Diagram DOM structure on board
- Verbally traverse to different elements
  - how to go up, down and sideways?
  - parent
  - ancestor
  - child
  - descendant
  - neighbor
  - first
  - last
- Resources:
  - https://api.jquery.com/category/traversing/tree-traversal/
  - http://www.w3schools.com/jquery/jquery_traversing.asp
  
#### Code Together: Selecting elements and adding styles
Find all `p` elements that are children of a `div` element and apply a border that is 1px wide, solid, and gray to the matching `p` elements.

```
<!-- Put this into your index.html page. Then open your index.html page in Chrome. Next open the Chrome console to try writing javascript that accomplishes the task. When would you place your code in the script tags below the content of the web page? -->

<p>one</p>
<div><p>two</p></div>
<p>three</p>
 
<script>
// Your code here.
</script>
```
<details><summary>Answer:</summary>
<p>

<code>$( "div > p" ).css( "border", "1px solid gray" );</code>
</p>
</details>

### Vanilla Javascript 
- what is it?
- Why use vanilla vs jQuery?

#### Vanilla Methods for selecting elements
- document.getElementById
- document.getElementsByTagName
- document.getElementsByClassName
- document.querySelector
- document.querySelectorAll
- and more...

#### Code Together: jQuery selectors for each of the above

#### You Do: Selecting DOM elements (use jQuery) (10 min)
https://github.com/ga-wdi-exercises/js-dom-quotes/tree/jquery

### Discussion: What is $(document).ready()?
```
 // A $( document ).ready() block.
$( document ).ready(function() {
    console.log( "ready!" );
});
```
- Access and manipulate a page safely. Things not working? Make sure the document is loaded by checking with...
- Hardly ever a use case where you do not use `$(document).ready()` to wrap your JS
- shortcut: `$(function(){}`

#### DOM Manipulation using jQuery

- create a button on your html page with a class of 'continue' and some text inside the button...

<details><summary>Get the `button` element with class `continue` and change it's text to "Next Step..."</summary>
<p>
<code>
$( "button.continue" ).html( "Next Step..." )
</code>
</p>
</details>


### jQuery Setters & Getters & jQuery docs
- When reading the jQuery docs, be sure to scroll through the whole document to ensure you're looking at the correct method signature. Some jQuery methods change their behavior depending on the number of arguments they have when called.
- Have a look at `.val()`. [(jQuery documentation on val())](http://api.jquery.com/val/). Note in the table of contents that there are two method signatures, .val() and.val(value). This is our hint that .val() can do two things.
- Reading the documentation, we discover that .val() is getter on an element, but that .val(value) is a setter on an element. Be sure you're using the correct method. Reading examples is very helpful, and the jQuery examples in the docs are fully functional!
- When would you want to get or set a value on a web page?

### Read and Discuss: Why use jQuery over directly working with a DOM object?
- reference: [learn.jquery.com](https://learn.jquery.com/using-jquery-core/jquery-object/)

### Read and Discuss: What happens if you get a javascript library conflict?
- reference: [learn.jquery.com](http://learn.jquery.com/using-jquery-core/avoid-conflicts-other-libraries/)

### Lab: Get the value of an input
```
<!-- Given this input, how do you get the value using jQuery? And what if the value changes? -->
<input type="text" value="some text">

```
<details><summary>Answer</summary>
<p> Simple: 
<code>console.log($("input").val())
  
  </code>
<p>Fancy: <code>$( "input" )
  .keyup(function() {
    var value = $( this ).val();
    $( "p" ).text( value );
  })
  .keyup();
  </code>
  </p>
  </details>
  
- Question: What if you had multiple inputs?

### Lab: Research Common jQuery Functions
Here is a list of some commonly used jQuery API functions:
1. find()
2. hide()
3. show()
4. html()
5. append()
6. prepend()
7. on()
8. submit()
9. css()
10. attr()
11. eq()
12. text()
13. each()
 
### jQuery function examples and method chaining
`eq()`
- resource: [api.jquery.com](https://api.jquery.com/eq/)
Given:
```
<ul>
  <li>list item 1</li>
  <li>list item 2</li>
  <li>list item 3</li>
  <li>list item 4</li>
  <li>list item 5</li>
</ul>
```
Which li is affected when the following code is executed?
`$( "li" ).eq( 2 ).css( "background-color", "red" );`
How about:
`$( "li" ).eq( -2 ).css( "background-color", "red" );`

[`each()`](http://api.jquery.com/jquery.each/)

[`submit()`](https://api.jquery.com/submit/)

### Homework
More Practice: [Try jQuery level 1](http://try.jquery.com/levels/1/sections/1)
Homework: https://github.com/ga-wdi-exercises/the-jquery-review

### Bonus Material

#### Web servers, browsers, static vs dynamic content

- What is the role of the browser?
- What is meant by client-server? Who / where / what is the client and who / where / what is the server?
 - To display web pages
   - reads the DOM and display it to the user
 - To interact with the DOM according to the instructions given by the web developer
 - To comply with standards and stay up to date (
  - examples: ES6 
   - IE - why is it hated?

- What is a web page?
- simply a collection of html elements, css and javascript, media, meta info
- represented by the document object
- displayable by the browser
- how do you reach a web page? Via a unique address
- what happens when you type in a unique address?
  - DNS lookup
  - sends request to web server
  - response & handshake, site is sent to your browser
  - When you type http://amazon.com into your browser's address bar and hit 'Go,' the browser (your 'client') makes a request to the server. It parses the response, then fetches all associated assets, like JavaScript files, stylesheets and images. It then assembles the page. If you click a link, it does the same process: fetch the page, fetch the assets, put it all together, show you the results. This is called the 'request response cycle.'

- What does the web server do?
  -  sends web page to you, the end user. millions of times.
- Server is comprised of: 
  - hardware (computer) that hosts a website 
  - and server software that responds to http requests (apache, nginx, etc)
  
- How do you publish a website?
  - To start, you need either a static or a dynamic web server.
  - A static web server, or stack, consists of a computer (hardware) with an HTTP server (software). We call it "static" because the server sends its hosted files "as-is" to your browser.
   - A dynamic web server consists of a static web server plus extra software, most commonly an application server and a database. We call it "dynamic" because the application server updates the hosted files before sending them to your browser via the HTTP server.
For example, to produce the final webpages you see in the browser, the application server might fill an HTML template with contents from a database. Sites like MDN or Wikipedia have many thousands of webpages, but they aren't real HTML documents, only a few HTML templates and a giant database. This setup makes it easier and quicker to maintain and deliver the content.
  - Web server is used to create the front end (html, css, media) of the application server. Program logic and database access occurs via the application server.
￼
further study: static vs dynamic sites. Pros and cons of each. When should you use each? Costs, speed, complexity...

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
