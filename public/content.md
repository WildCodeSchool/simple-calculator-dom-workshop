# DOM manipulation workshop 

## Simple calculator V2

#### Introduction

The purpose of this workshop is to discover DOM manipulation. It will directly follow the first simple calculator workshop.

#### Concepts

During this workshop, we will learn to :

- Get value of a form field in JS
- Listen to user interaction on a button
- Add text to an element

#### Starting point

Start from the first [simple calculator workshop](https://wildcodeschool.github.io/simple-calculator-workshop/). You should already have a simple *index.html* file with HTML structure and JS code in a `<script>` tag.

First, you will move the JS code from HTML file to a dedicated JS file (it is a best practice to separate HTML and JS in different files).
Create a file named *script.js* and cut and paste all the javascript code into this new file (juste JS code, do not paste the HTML `<script>` tags)

At the end of the *index.html*, before the `</body>` closing tag, add a "src" attribute to the remaining `<script>` tag to link the js file to the *index.html*.

Also add a `<h1>` title to your *index.html*.

> You are ready to start ! Wait for the correction or help your classmates

#### Get value from a form field

In the JS code, users enter first, second value and operand, using a `prompt()`. Now you want to have form fields in the HTML page instead.

Add two `<input>` (with the correct type attribute !) for first and second value. 
Add a `<select>` field with the 4 operands.

Do not forget to add and link a `<label>` for each field. 

To access the fields' value, we can leverage the `id` attribute of the inputs and use the DOM method `document.getElementById('your_id');`. It will retrieve the whole element (not only its value, but all its characteristics, like the style, the position in the page, etc.)

**Warning:** An **id** has to be **unique** ! You can not have several ids with the same value in your HTML page.

In our case, we only want to get the value entered in the input. Thus, you should write `document.getElementById('your_id').value` and you will get the value.

In the JS code, remove the `prompt()` parts and replace it with JS code to get value from each inputs.

**Remark:** `parseInt()` functions are still mandatory because, like prompt, field values are always considerated as *strings*, even if you enter a number.

> Wait for the correction or help your classmates

#### Listen to user interaction on a button

At this step, when you enter a new operation, `console.log()` does not show any result. However if you refresh your page, input values are kept and the result will be correct. 

In order to have a more user friendly approach, we will add a new "calculate" button. When user will click on this button, it will retrieve current input values and launch the arithmetic operation.

First, add this new "calculate" button in *index.html*.

Then, in *script.js*, you have to **listen** when the user will click on this button. To do that, you have to **attach** an *eventListener* to the element you want to monitor. An *eventListener* is a function which will be executed when a specific event is triggered on a specific element. What is an event ? it could be a click, a mouse hovering an element, a double click, a keyboard interaction, a scroll, etc. [Exhaustive list of events](https://developer.mozilla.org/en-US/docs/Web/Events).

```js
// get a DOM element with id="my_button"
let myButton = document.getElementById('my_button'); 
// attach a "click" event listener to this element
myButton.addEventListener('click', function(event) { 
    // some code here, that will be executed each time you click on myButton 
});

// get a DOM element with id="beautiful_picture"
let myImage = document.getElementById('beautiful_picture');
// attach a "hover" event listener to this element
myButton.addEventListener('hover', function (event) { 
    // some code here, that will be executed each time you put your cursor over this image 
});
```

As you can see, the function `addEventListener()` has 2 parameters. First one is the event type, second is a function to execute if the event occurs on the element.
It is a function which is a parameter of another function... Yes! It might be a bit confusing at first, but you will quickly become very familiar with this concept ! 

Another particularity, this second function can be defined without a name between *function* keyword and parenthesis (**anonymous function**). 

**Remark:** This anonymous function can take an optional parameter ("event" in the code above). It won't be useful in this simple exercise, so you can just ignore it **for now**.

Add an *eventListener* on the new 'calculate' button, which will trigger the previous code when the button is clicked.

In the browser console, you should see the result of the different operations each time you click on the button.

> Wait for the correction or help your classmates

#### Add text to an element

Browser console is great, but it could be even better if you could see the result directly on the page.

To change the content inside an element, you should use the innerHTML property of this element. 
```html
    <div id="firstname">John</div>
```
```js
    document.getElementById('firstname').innerHTML = 'Bob'; // will retrieve the element with id="firstname" and replace the actual content 'John' by 'Bob'
```

First, create a `<div>` with a 'result' *id*, below the calculate button.
Then you want to add text in this element. 

In the javascript file, initialize a variable 'result'. Then replace all the console log to store each operation result in this new variable.
Then use `innerHTML` to write this result inside the HTML element with 'result' id.

And that's all ! you have a very basic calculator !

> Wait for the correction, help your classmates, or try to work on the bonus below

#### Bonus

- Display an error in the "result" element if you try to divide a number per zero.
- Add some style using CSS.
