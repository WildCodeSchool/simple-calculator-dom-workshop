# DOM manipulation workshop 

## Simple calculator V2

#### Introduction

The purpose of this workshop is to discover the DOM manipulation. It will directly follow the first simple calculator workshop.

#### Concepts

During this workshop, we will learn to :

- Get value from a form field in JS
- Listen to user interaction with a button
- Add text to an element

#### Starting point

Start from the first [simple calculator workshop](https://wildcodeschool.github.io/simple-calculator-workshop/). You should already have a simple *index.html* file with HTML structure and JS code in a `<script>` tag.

First, you will move the JS code from HTML file to a dedicated JS file (it is a best practice to separate HTML and JS in different files).
Create a file named *script.js* and cut and paste all the javascript code into this new file (juste JS code, do not paste the HTML `<script>` tags)

At the end of the *index.html*, before the `</body>` closing tag, add a "src" attribute to the remaining `<script>` tag to link the js file to the *index.html*.

Also add a `<h1>` title to your *index.html*, then you should have 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple calculator</title>
</head>
<body>
    <h1>Simple calculator</h1>
    <script src="script.js"></script>
</body>
</html>
```

your *script.js* file should be 

```js
  let firstValue = prompt('First value:');
  firstValue = parseInt(firstValue);
  let secondValue = prompt('Second value:');
  secondValue = parseInt(secondValue);
  let operand = prompt('Operand:');

  switch (operand) {
    case '+':
      console.log(firstValue + secondValue);
      break;
    case '-':
      console.log(firstValue - secondValue);
      break;
    case '*':
      console.log(firstValue * secondValue);
      break;
    case '/':
      console.log(firstValue / secondValue);
      break;
    default:
      console.log('Invalid operator');
  }
```


#### Get value from a form field

In the JS code, users enter first, second value and operand, using a `prompt()`. Now you want to have form fields in the HTML page instead.

Add two `<input>` (it would be interesting to use the "number" type) for first and second value. 
Add a `<select>` field with the 4 operands.

Do not forget to add and link a `<label>` for each field. To link label and field element, you have to use an `id` attribute. 

You should get this : 
```html
<body>
    <h1>Simple calculator</h1>
        <label for="firstValue">Number 1</label>
        <input type="number" id="firstValue">

        <label for="operand">Operand</label>
        <select id="operand">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="/">/</option>
            <option value="*">*</option>
        </select>

        <label for="secondValue">Number 2</label>
        <input type="number" id="secondValue">
    <script src="script.js"></script>
</body>

```

This **id** is also mandatory to access the field value with the help of Javascript.

How to do this ? You should use the JS method `document.getElementById('your_id');` and it will retrieve the whole element (not only its value, but all its characteristics, like the style, the position in the page, etc.)

**Warning:** an **id** has to be **unique** ! You can not have several ids with the same value in your HTML page.

In our case, we only want to get the value entered in the input. Thus, you should write `document.getElementById('your_id').value` and you will get the value.

In the JS code, remove the `prompt()` parts and replace it with JS code to get value from each inputs.

You should have this code :
```js
    let firstValue = document.getElementById('firstValue').value;
    firstValue = parseInt(firstValue);

    let secondValue = document.getElementById('secondValue').value;
    secondValue = parseInt(secondValue);
    
    let operand = document.getElementById('operand').value;
```

**Remark:** `parseInt()` functions are still mandatory because, like prompt, field values are always considerated as *strings*, even if you enter a number.


#### Listen to user interaction with a button

At this step, when you enter a new operation, `console.log()` does not show any result. However if you refresh your page, input values are keeped and the result will be correct. 

In order to have a more user friendly approach, we will add a new "calculate" button. When user will click on this button, it will check actual values of inputs and launch the arithmetic operation.

First, add this new "calculate" button in *index.html*.

Then, in *script.js*, you have to **listen** when the user will click on this button. To do that, you have to **attach** an *eventListener* to the element you want to monitor. An *eventListener* is a function which will listen if a specific event is triggered an a specific element. What is an event ? it could be a click, a mouse hovering an element, a double click, a keyboard interaction, a scroll, etc. [Exhaustive list of events](https://developer.mozilla.org/en-US/docs/Web/Events).

```js
// get a DOM element with id="my_button"
let myButton = document.getElementById('my_button'); 
// attach a "click" event to this element
myButton.addEventListener('click', function(event) { 
    // some code here, will be execute each time you click on myButton 
});

// get a DOM element with id="beautiful_picture"
let myImage = document.getElementById('beautiful_picture');
// attach a "hover" event to this element
myButton.addEventListener('hover', function (event) { 
    // some code here, will be execute each time you hover this image 
});

```

As you can see, the function `addEventistener()` has 2 parameters. First one is the event type, second is a function to execute if the event occurs on the element.
It is a function which is a parameter of another function... yes! it is a bit confusing at first, but you will quickly become very familiar with this concept ! 

Another particularity, this second function could be defined without a name. It is called an **anonymous function**, without name between *function* keyword and parenthesis. 

**Remark:** This anonymous function can take an optionnel parameter ("event" in the code above). It would not be useful here in this simple exercise, but it is a good practice to specify it. However, you can ignore it right now.

Add an *eventListener* on the new 'calculate' button, which will trigger all the previous code when the button is clicked.

You should obtains this code : 
```js
document.getElementById('calculate').addEventListener('click', function(event) {
    let firstValue = document.getElementById('firstValue').value;
    firstValue = parseInt(firstValue);

    let secondValue = document.getElementById('secondValue').value;
    secondValue = parseInt(secondValue);
    
    let operand = document.getElementById('operand').value;
    let result = '';

    switch (operand) {
        case '+':
        console.log(firstValue + secondValue);
        break;
        case '-':
        console.log(firstValue - secondValue);
        break;
        case '*':
        console.log(firstValue * secondValue);
        break;
        case '/':
        console.log(firstValue / secondValue);
        break;
        default:
        console.log('Invalid operator');
    }
});

```
In the browser console, you can see result of the different operations each time you click on the button.

#### Add text to an element

Browser console is great, but it could be even better if you could see the result directly in the HTML page.

To change the content inside an element, you should use the innerHTML property of this element. 
```html
    <div id="firstname">John</div>
```
```js
    document.getElementById('firstname').innerHTML = 'Bob'; // will retrieve the element with id="firstname" and replace the actual content 'John' by 'Bob'
```

First, create a `<div>` with a 'result' *id*, below the calculate button.
Then you want to add text in this element. 

In your javascript, initialize a variable 'result'. Then replace all the console log to store each operation result in this new variable.
Then use `innerHTML` to write this result inside the HTML element with 'result' id.

```html
        <button id="calculate">=</button>
        <div id="result"></div>
```

```js
    let result = '';

    switch (operand) {
        case '+':
            result = firstValue + secondValue;
            break;
        case '-':
            result = firstValue - secondValue;
            break;
        case '*':
            result = firstValue * secondValue;
            break;
        case '/':
            result = firstValue / secondValue;
        default:
            result = 'Invalid operator';
    }

    document.getElementById('result').innerHTML = result;

```

And that's all ! you have a very basic calculator !

As a bonus, you can add some style, adding a CSS file.
You can also display an error in the "result" element if you try to divide a number per zero.