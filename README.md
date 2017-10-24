<!--Damn it, just closed out of all my timing notes for WDI4 --started at 9:31, ended at 10:47, time started slipping toward the end, demo pieces are shorter than time given...exercise pieces are longer than time given -->
<!--9:46 WDI3 -->
<!--9:30 5 minutes-->

<!--WDI5 1:52 -->
<!--Hook: Remember ES6?  Today we are going to run through the rest of the major improvements of ES6, and we will wrap up with an ES6 quiz.  These improvements will help you DRY out your code, and put a little more power into your 3rd Projects.-->

# ES6 Part 2

## Objectives
*By the end of this lesson, students will be able to:*

- **Compare/contrast** features of ES5 and ES6
- **Shorten** methods and properties with new ES6 syntax
- **Use** template literals to minimize string concatenation
- **Use** arrow functions to simplify anonymous function definitions
- **Use** the spread operator to manage an array of input

<!--9:47 -->
<!--9:35 5 minutes -->

### Concise Object Properties and Methods

ES6 allows us to shorten method definitions from:

```js
var car = {
  drive: function(){
    console.log("vroom")
  }
}
```

to

```js
let car = {
  drive(){
    console.log("vroom")
  }
}
```

And for properties where the key is the same as the variable storing the value:

```js
// es5
let x = 1
let y = 2
let obj = {x:x, y:y}

// vs
//es6

let obj = {x,y}
```

<!--9:51 WDI3 -->
<!--9:40 5 minutes -->

#### You do: Concise methods and properties practice

Use both of these concise syntaxes in the exercise below:

1. https://github.com/ga-wdi-exercises/es6-exercises/blob/master/07-concise-properties-and-methods.js

<!--WDI5 2:02  -->
<!--9:56 WDI3 -->
<!--9:45 5 minutes -->

### Template Literals

Remember string concatenation in Javascript?

```js
var name = "Inigo Montoya"
var killee = "father"
var prepareTo = "die"

console.log("Hello. My name is "+ name + ". You killed my " + killee +". Prepare to " + prepareTo)
```

Annoying to try and remember all of those `+` signs right?  In ES6, we can interpolate variables using template literal syntax:

```js
let name = "Inigo Montoya"
let killee = "father"
let prepareTo = "die"

console.log(`Hello. My name is ${name}. You killed my ${killee}. Prepare to ${prepareTo}`)
```

Way easier, right?

<!-- 10:00 WDI3 -->
<!-- Actually 9:27 WDI2-->

<!--9:50 10 minutes -->

#### You do: Template Exercise

1. https://github.com/ga-wdi-exercises/es6-exercises/blob/master/09-templates.js

<!--WDI5 2:14  -->
<!--10:10 WDI3 -->
<!--10:00 10 minutes -->

### Arrow Functions

Arrow functions are a new shorthand syntax for defining anonymous functions:

```js
let foods = ["pizza","mac n cheese","lasagna"]
foods.forEach( food => console.log(`I love ${food}`) )

// vs the old

foods.forEach(function(food){
  console.log("I love " + food)
})
```

If there is more than one argument to the anonymous function, wrap
them in parens:

```js
let foods = ["pizza","mac n cheese","lasagna"]
foods.forEach( (food,i) => console.log(`My #${i} favorite food is ${food}`) )
```

Arrow functions also have the benefit of lexical scoping, which is a fancy way of saying it uses “this” from the surrounding code: the code that contains the code in question.  See how this can be helpful below:

```js
//Function scoped in ES5
var pizza = {
  temperature: 0,
  toppings: ["cheese", "ham", "pineapple"],
  bake() {
    setInterval(function(){
      this.temperature++ // doesn't work because this is GLOBAL. The setInterval function belongs to the window object.
    }, 1000)
  }
}

// vs Lexically Scoped in ES6

var pizza = {
  temperature: 0,
  toppings: ["cheese", "ham", "pineapple"],
  bake() {
    setInterval( () => {
      this.temperature++
    }, 1000)
  }
}
```

Additionally, the `return` statement is not needed with single line arrow functions. There is an implicit return.

```js
let add = (x, y) => x + y
```

If the function is multi-line, you need to explicitly return:

```js
let add = (x,y) => {
  console.log(x + y)
  return x + y
}
```

<!--Actually 6 mins back WDI2 -->
<!-- 10:18 WDI3 -->
<!-- 10:10 10 minutes -->

#### You do: Arrow functions

> **Hint:** If you are stuck on the `reduce` part of the exercise below, remember you can include an initial value after your arrow function (0 perhaps?).

1. https://github.com/ga-wdi-exercises/es6-exercises/blob/master/11-arrow-functions.js

<!--WDI5 2:34  -->
<!--10:20 10 minutes -->

### Spread operator

The spread operator `...` allows an expression to be expanded into multiple elements.

This is useful for separating an array into individual elements:

```js
let dimensions = [10, 5, 2];
let volume = function(height, width, length){
  return height * width * length;
}
volume(...dimensions);

// versus

volume(dimensions[0], dimensions[1], dimensions[2])
```

This also makes it very easy to create copies of an array in functions where
mutation occurs:

```js
var days = ["monday","tuesday","wednesday","thursday","friday","saturday","sunday"]
function reversedDays(arr){
  return arr.reverse()
}
console.log(reversedDays(days))
// but now days is no longer in order
console.log(days)

// To deal with this, we can either:

function reversedDays(arr){
  var newArray = []
  for(let i = 0; i < arr.length; i++){
    newArray.push(arr[i])
  }
  return newArray.reverse()
}
console.log(reversedDays(days))
console.log(days)

// or... (<- pun)

function reversedDays(arr){
  return [...arr].reverse()
}
console.log(reversedDays(days))
console.log(days)
```

<!--10:30 5 minutes -->

#### You do: Spread Practice

**Challenge:** How might you use template literals, a spread operator, and an array of `name`, `day`, and `adjective`, to make a greeting function that prints out:

`Hello, Zeb, today is Tuesday, isn't it a wonderful day?`

Tweak the values of those variables and test it again.

<!--WDI5 2:52 -->
<!--10:47 WDI3 -->
<!--10:35 5 minutes -->

## Legacy Browser Support

Support for ES6 is great! - https://kangax.github.io/compat-table/es6/

If you need to support a legacy browser, check out the following tools:
- [Traceur](https://github.com/google/traceur-compiler/wiki/Getting-Started)
- [Babel](https://babeljs.io/)

## Keep Going

There are lots more features of ES6 that we have not covered:

- [Symbols](http://es6-features.org/#SymbolType)
- [Iterator & for..of operator](http://es6-features.org/#IteratorForOfOperator)
- [Generators](https://davidwalsh.name/es6-generators)
- [Proxies](https://ponyfoo.com/articles/es6-proxies-in-depth)
- [Reflection and meta-programming](http://www.2ality.com/2011/01/reflection-and-meta-programming-in.html)

## Resources

- [You Don't Know ES6](https://github.com/getify/You-Dont-Know-JS/tree/master/es6%20%26%20beyond)
- [Block Scope](https://www.sitepoint.com/joys-block-scoping-es6/)
- [Destructuring](http://www.2ality.com/2015/01/es6-destructuring.html)
- [Template Literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals)

<!--10:50 WDI3 -->
