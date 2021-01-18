

# HTML

&lt;!DOCTYPE html>  using html5

**Document Object Model**

Tree like structure describe html elements

**Common HTML Tags**

**Head -> title**: browser page title

**h1, h2, .. , h6**: page title

**ol, ul **-> li: ordered list, unordered list; li item in list

**img**: required attributes: **src, alt **(if image doesn’t load)**,** does not need closing tag. Optional attributes: **width**

**a**: link attribute:href   &lt;a href="index.html">A link&lt;/a>

**table**: 



*   **thead**, head of the table
    *   tr, table row
        *   th, column names
*   tbody
    *   tr, table row
        *   td, table cells

**form**: User input



*   type: How user input. E.g. text, submit, password, radio
*   placeholder
*   name: How developers access user input.

<table>
  <tr>
   <td>
<code>   &lt;form></code>
<p>
<code>        &lt;input type="text" placeholder="First Name" name="first"></code>
<p>
<code>        &lt;input type="password" placeholder="Password" name="password"></code>
<p>
<code>        &lt;div></code>
<p>
<code>            Favorite Color:</code>
<p>
<code>            &lt;input name="color" type="radio" value="blue"> Blue</code>
<p>
<code>            &lt;input name="color" type="radio" value="green"> Green</code>
<p>
<code>            &lt;input name="color" type="radio" value="yellow"> Yellow</code>
<p>
<code>            &lt;input name="color" type="radio" value="red"> Red</code>
<p>
<code>        &lt;/div></code>
<p>
<code>        &lt;input type="submit"></code>
<p>
<code>    &lt;/form></code>
   </td>
  </tr>
  <tr>
   <td><code>Drop down</code>
<p>
<code>JS:</code>
<p>
<code>document.querySelector('select').onchange = function() {</code>
<p>
<code>  document.querySelector('#hello').style.color = this.value;</code>
<p>
<code>}</code>
<p>
<code>HTML:</code>
<p>
<code>&lt;select> \
&lt;option value="black">Black&lt;/option> \
&lt;option value="red">Red&lt;/option></code>
<p>
<code>&lt;/select></code>
   </td>
  </tr>
</table>




*   

**div**: Logical section in html


# CSS

Stylize HTML page

**Inline CSS attributes**

Using style attributes.

e.g.      &lt;h2 style="color: blue; text-align: center;">Ordered List:&lt;/h2>

Style can be inherited from the parent DOM element.

**Inline head tags**

E.g.


```
<style>
 h1 { color: blue; text-align: center; }
</style>
```


**Standalone CSS file**

E.g.


<table>
  <tr>
   <td>.Css file
   </td>
   <td> h1 { color: blue; text-align: center; }
   </td>
  </tr>
  <tr>
   <td>head element
   </td>
   <td>&lt;link rel=”stylesheet” href=”styles.css”>
   </td>
  </tr>
</table>


**Common CSS Properties**



*   color;background-color
*   Text-align
*   Width,height
*   Margin (outside), padding (inside)
*   font-family, font-size, font-weight
*   border

**Identifying Elements**


<table>
  <tr>
   <td>Html attributes
   </td>
   <td>Css selector
   </td>
  </tr>
  <tr>
   <td>id=”foo”, unique in html
   </td>
   <td>#foo
   </td>
  </tr>
  <tr>
   <td>class=”baz”, similar to id, but not uniq
   </td>
   <td>.baz
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>
   </td>
  </tr>
</table>


[https://www.w3schools.com/cssref/css_selectors.asp](https://www.w3schools.com/cssref/css_selectors.asp)

a, b Multiple Element Selector

a b Descendant Selector

a > b Child Selector

a + b Adjacent Sibling Selector

[a=b] Attribute Selector

a:b Pseudoclass Selector, e.g. button:hover {}  ⇐ when button is hovered

a::b Pseudoelement Selector

**Specificity - priority when multiple css selector points to same html element**



1. Inline
2. Id
3. Class
4. Type


## Responsive Design

Make sure page look good on mobile or other platform

**Viewport**

&lt;meta name="viewport" content="width=device-width, initial-scale=1.0">

Scale html element to screen width

**Media Queries**

• Media Types: print, screen, ... 

• Media Features: height, width, orientation

@media (min-width: 600px) {

  ...

}

@media (max-width: 599px) {

  …

}

**Flexbox**

Wrap around if not enough room

{

  display: flex;

  flex-wrap: wrap;

}


## Bootstrap

Powerful css library


## Sass (.scss file)

Extension to css



*   Use variables in css
*   Nesting css selector
*   inheritance
*   Need to translate into css using “sass”, e.g. > sass f.scss:f.css

<table>
  <tr>
   <td>
$color: red;
<p>
ul {
<p>
  color: $color;
<p>
}
   </td>
  </tr>
  <tr>
   <td>div {
<p>
  font-size: 18px;
<p>
  p {color:blue};
<p>
  ul {color:green};
<p>
}
   </td>
  </tr>
  <tr>
   <td>%message {
<p>
  Font-family: sans;
<p>
  Font-size: 18px;
<p>
}
<p>
.success {
<p>
  @extend %message;
<p>
  Background-color: green;
<p>
}
   </td>
  </tr>
</table>



# Javascript

&lt;script> tag in HTML

**Events**

•onclick 

•onmouseover 

•onkeydown 

•onkeyup 

•onload 

•onblur

.onsubmit (html forms, set return false if only running local)


<table>
  <tr>
   <td>&lt;head>
<p>
  &lt;script>
<p>
     function hello() {alert(‘hello’)}
<p>
  &lt;/script>
<p>
&lt;/head>
   </td>
  </tr>
  <tr>
   <td>&lt;body>
<p>
   &lt;button onclick=”hello()”>Click Here&lt;/button>
<p>
&lt;/body>
   </td>
  </tr>
  <tr>
   <td>document.addEventListener(‘DOMContentLoaded’, function() {  // Make sure HTML is loaded
<p>
  document.querySelector(‘button’).onclick = hello
<p>
}
   </td>
  </tr>
</table>


**querySelector**

Lookup and extract HTML element (first one if there are multiple)

•document.querySelector('tag') 

•document.querySelector('#id') 

•document.querySelector('.class')


```
document.querySelector('h1').innerHTML = 'Goodbye!';
```


•document.querySelectorAll(‘...’)  (select all elements into a Node List)


```
document.querySelectorAll('button').forEach(function(button) {
                button.onclick = function() {
                    document.querySelector("#hello").style.color = button.dataset.color;
                }
            });
```


**Templated String**

Javascript equivalent of f-string: `Count is now ${counter}`

**Data Attributes**

use the `data-SOMETHING` attribute to assign data to an HTML element. We can later access that data in JavaScript using the element’s `dataset` property.


<table>
  <tr>
   <td>HTML
<p>
<code>    &lt;button data-color="red">Red&lt;/button></code>
<p>
<code>    &lt;button data-color="blue">Blue&lt;/button></code>
<p>
<code>    &lt;button data-color="green">Green&lt;/button></code>
   </td>
  </tr>
  <tr>
   <td>JS
<p>
<code>                   document.querySelector("#hello").style.color = button.dataset.color;</code>
   </td>
  </tr>
</table>


**Arrow Functions: Simplified function definition**

use [Arrow Functions](https://www.w3schools.com/js/js_arrow_function.asp) where we have an input (or parentheses when there’s no input) followed by `=>` followed by some code to be run.


<table>
  <tr>
   <td><code>// Anonymous functions</code>
<p>
<code>document.addEventListener('DOMContentLoaded', () => {</code>
<p>
<code>    document.querySelectorAll('button').forEach(button => {</code>
<p>
<code>        button.onclick = () => {</code>
<p>
<code>            document.querySelector("#hello").style.color = button.dataset.color;</code>
<p>
<code>        }</code>
<p>
<code>    });</code>
<p>
<code>});</code>
   </td>
  </tr>
  <tr>
   <td><code>// Named functions</code>
<p>
<code>count = () => {</code>
<p>
<code>    counter++;</code>
<p>
<code>    document.querySelector('h1').innerHTML = counter;</code>
<p>
<code>    </code>
<p>
<code>    if (counter % 10 === 0) {</code>
<p>
<code>        alert(`Count is now ${counter}`)</code>
<p>
<code>    }</code>
<p>
<code>}</code>
   </td>
  </tr>
</table>


**Update HTML through JS**

const li = document.CreateElement(‘li’)

li.innerHTML  =’new content’

document.querySelector(#task).append(li);

**Disable HTML element**

document.querySelector(‘...’).disable = true

**Intervals**

setInterval(func, 1000) - run func every 1000 ms

**Local Storage**

localstorage.getItem(key)

localStorage.setItem(key, value)

**JSON - JS Object Notation**

**AJAX**

Update page after load


```
document.addEventListener('DOMContentLoaded', function() {
    // Send a GET request to the URL
    fetch('https://api.exchangeratesapi.io/latest?base=USD')
    // Put response into json form
    .then(response => response.json())
    .then(data => {
        // Log data to the console
        console.log(data);
    });
});
```

