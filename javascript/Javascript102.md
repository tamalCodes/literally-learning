
<!-- TOC -->

- [What is the difference between Call, Apply and Bind](#what-is-the-difference-between-call-apply-and-bind)
- [What is JSON and its common operations](#what-is-json-and-its-common-operations)
- [Slice, Splice 👇🏻](#slice-splice-)
  - [What is the purpose of the array slice method](#what-is-the-purpose-of-the-array-slice-method)
  - [What is the purpose of the array splice method](#what-is-the-purpose-of-the-array-splice-method)
  - [What is the difference between slice and splice](#what-is-the-difference-between-slice-and-splice)
- [How do you compare Object and Map](#how-do-you-compare-object-and-map)
- [What is the difference between == and === operators](#what-is-the-difference-between--and--operators)
- [Functions 👇🏻](#functions-)
  - [What are lambda or arrow functions](#what-are-lambda-or-arrow-functions)
  - [What is a first class function](#what-is-a-first-class-function)
  - [What is a first order function](#what-is-a-first-order-function)
  - [What is a higher order function](#what-is-a-higher-order-function)
  - [How Higher Order Functions Work](#how-higher-order-functions-work)
  - [What is a unary function](#what-is-a-unary-function)
  - [Pure functions](#pure-functions)
    - [Advantages of pure functions](#advantages-of-pure-functions)
  - [Impure Functions](#impure-functions)
    - [Advantages of impure functions](#advantages-of-impure-functions)
- [Let VS Var](#let-vs-var)
- [How do you redeclare variables in switch block without an error](#how-do-you-redeclare-variables-in-switch-block-without-an-error)
- [What is memoization](#what-is-memoization)
  - [How Does Memoization Work?](#how-does-memoization-work)
  - [Closure](#closure)
  - [High Order Function](#high-order-function)
  - [Importance of Memoization](#importance-of-memoization)
  - [When to Use Memoization?](#when-to-use-memoization)
- [What is Hoisting](#what-is-hoisting)
- [What are closures](#what-are-closures)
- [What is a service worker](#what-is-a-service-worker)
- [How do you manipulate DOM using a service worker](#how-do-you-manipulate-dom-using-a-service-worker)
- [How do you reuse information across service worker restarts](#how-do-you-reuse-information-across-service-worker-restarts)

<!-- /TOC -->

# What is the difference between Call, Apply and Bind

The difference between Call, Apply and Bind can be explained with below examples,

**Call:** The call() method invokes a function with a given `this` value and arguments provided one by one

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };
function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}
invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How you?
invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How you?
```

**Apply:** Invokes the function with a given `this` value and allows you to pass in arguments as an array

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
```

**bind:** returns a new function, allowing you to pass any number of arguments

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

var inviteEmployee1 = invite.bind(employee1);
var inviteEmployee2 = invite.bind(employee2);
inviteEmployee1("Hello", "How are you?"); // Hello John Rodson, How are you?
inviteEmployee2("Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

Call and apply are pretty interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.

Whereas Bind creates a new function that will have `this` set to the first parameter passed to bind().

  

# What is JSON and its common operations

**JSON** is a text-based data format following JavaScript object syntax, which was popularized by `Douglas Crockford`. It is useful when you want to transmit data across a network and it is basically just a text file with an extension of .json, and a MIME type of application/json

**Parsing:** Converting a string to a native object

```javascript
JSON.parse(text);
```

**Stringification:** converting a native object to a string so it can be transmitted across the network

```javascript
JSON.stringify(object);
```

# Slice, Splice 👇🏻

## What is the purpose of the array slice method

The **slice()** method returns the selected elements in an array as a new array object. It selects the elements starting at the given start argument, and ends at the given optional end argument without including the last element. If you omit the second argument then it selects till the end.

Some of the examples of this method are,

```javascript
   let arrayIntegers = [1, 2, 3, 4, 5];
   let arrayIntegers1 = arrayIntegers.slice(0, 2); // returns [1,2]
   let arrayIntegers2 = arrayIntegers.slice(2, 3); // returns [3]
   let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
```

**Note:** Slice method won't mutate the original array but it returns the subset as a new array.

  

## What is the purpose of the array splice method

The **splice()** method is used either adds/removes items to/from an array, and then returns the removed item. The first argument specifies the array position for insertion or deletion whereas the optional second argument indicates the number of elements to be deleted. Each additional argument is added to the array.

   Some of the examples of this method are,

   ```javascript
   let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
   let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
   let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

   let arrayIntegers1 = arrayIntegersOriginal1.splice(0, 2); // returns [1, 2]; original array: [3, 4, 5]
   let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
   let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
   ```

   **Note:** Splice method modifies the original array too and returns the deleted array.

  

## What is the difference between slice and splice

Some of the major difference in a tabular form

| Slice                                        | Splice                                          |
| -------------------------------------------- | ----------------------------------------------- |
| Doesn't modify the original array(immutable) | Modifies the original array(mutable)            |
| Returns the subset of original array         | Returns the deleted elements as array           |
| Used to pick the elements from array         | Used to insert or delete elements to/from array |

  

# How do you compare Object and Map

**Objects** are similar to **Maps** in that both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. Due to this reason, Objects have been used as Maps historically. But there are important differences that make using a Map preferable in certain cases.

1. The keys of an Object are Strings and Symbols, whereas they can be any value for a Map, including functions, objects, and any primitive.
2. The keys in Map are ordered while keys added to Object are not. Thus, when iterating over it, a Map object returns keys in order of insertion.
3. You can get the size of a Map easily with the size property, while the number of properties in an Object must be determined manually.
4. A Map is an iterable and can thus be directly iterated, whereas iterating over an Object requires obtaining its keys in some fashion iterating over them.
5. An Object has a prototype, so there are default keys in the map that could collide with your keys if you're not careful. As of ES5 this can bypassed by using map = Object.create(null), but this is seldom done.
6. A Map may perform better in scenarios involving frequent addition and removal of key pairs.

  

# What is the difference between == and === operators

JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,

1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
2. Two numbers are strictly equal when they are numerically equal. i.e, Having the same number value.
      There are two special cases in this,
1. NaN is not equal to anything, including NaN.
2. Positive and negative zeros are equal to one another.
3. Two Boolean operands are strictly equal if both are true or both are false.


Some of the example which covers the above cases,

```javascript
0 == false   // true
0 === false  // false
1 == "1"     // true
1 === "1"    // false
null == undefined // true
null === undefined // false
'0' == false // true
'0' === false // false
[]==[] or []===[] //false, refer different objects in memory
{}=={} or {}==={} //false, refer different objects in memory
```

# Functions 👇🏻 

## What are lambda or arrow functions

An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.

   

## What is a first class function

In Javascript, functions are first class objects. First-class functions means when functions in that language are treated like any other variable.

For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable. For example, in the below example, handler functions assigned to a listener

```javascript
  const handler = () => console.log("This is a click handlerfunction");
  document.addEventListener("click", handler);
```

   

## What is a first order function

First-order function is a function that doesn’t accept another function as an argument and doesn’t return a function as its return value.

```javascript
const firstOrder = () => console.log("I am a function!");
```

   

## What is a higher order function

Higher-order function is a function that accepts another function as an argument or returns a function as a return value or both.

```javascript
// Callback function, passed as a parameter in the higher order function
function callbackFunction(){
    console.log('I am  a callback function');
}

// higher order function
function higherOrderFunction(func){
    console.log('I am higher order function')
    func()
}

higherOrderFunction(callbackFunction);
```

## How Higher Order Functions Work

So, suppose I want you to write a function that calculates the area and diameter of a circle. As a beginner, the first solution that comes to our mind is to write each separate function to calculate area or diameter.

```js

const radius = [1, 2, 3];

// function to calculate area of the circle
const calculateArea =  function (radius) {
    const output = [];
    for(let i = 0; i< radius.length; i++){
        output.push(Math.PI * radius[i] * radius[i]);
    }
    return output;
}

// function to calculate diameter of the circle
const calculateDiameter =  function (radius) {
    const output = [];
    for(let i = 0; i< radius.length; i++){
        output.push(2 * radius[i]);
    }
    return output;
}

console.log(calculateArea(radius));
console.log(calculateDiameter(radius))

```

But have you noticed the problem with the above code? Aren't we writing almost the same function again and again with slightly different logic? Also, the functions we have written aren't reusable, are they?

So, let's see how we can write the same code using HOFs:

```js
const radius = [1, 2, 3];

// logic to clculate area
const area = function(radius){
    return Math.PI * radius * radius;
}

// logic to calculate diameter
const diameter = function(radius){
    return 2 * radius;
}

// a reusable function to calculate area, diameter, etc
const calculate = function(radius, logic){ 
    const output = [];
    for(let i = 0; i < radius.length; i++){
        output.push(logic(radius[i]))
    }
    return output;
}


console.log(calculate(radius, area));
console.log(calculate(radius, diameter));
```

Now, as you can see in the above code, we have only written a single function calculate() to calculate the area and diameter of the circle. We only need to write the logic and pass it to calculate() and the function will do the job.

The code that we have written using HOFs is concise and modular. Each function is doing its own job and we are not repeating anything here.
   

## What is a unary function

Unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for a single argument accepted by a function.

Let us take an example of unary function,

```javascript
const unaryFunction = (a) => console.log(a + 10); // Add 10 to the given argument and display the value
```

   

## Pure functions

In simple terms, pure functions do not have an internal state. Therefore, all operations performed in pure functions are not affected by their state. As a result, the same input parameters will give the same deterministic output regardless of how many times you run the function.

```js

function add(a,b) { 
  return a + b
}
console.log(add(4,5))

```

This example contains a simple add() function, which gives 9 as the output. It is a very predictable output, and it does not depend on any external code. This makes the add() function a pure function.

If a function is declared pure and does not have a state, it can share many instances inside a class. Also, it is advised to avoid mutations inside pure functions.


### Advantages of pure functions
- A pure function works as an independent function that gives the same output for the same inputs.
- Pure functions are readable because of independent behavior. Moreover, they are straightforward to debug.
- You can clone an external state into a pure function, but it does not change the purity of the function.


## Impure Functions

An impure function is a function that contains one or more side effects. It mutates data outside of its lexical scope and does not predictably produce the same output for the same input.

```js

var addNew = 0;

function add(a,b){ 
  addNew =1; 
  return a + b + addNew
}

console.log(add(4,5))
```
   
In the above example, there is a variable named addNew, and it is declared outside of the add() function. But the state of that variable is changed inside the add() function. So, the add() function has a side effect on a variable outside of its scope and is therefore considered an impure function.

JavaScript doesn’t adhere to rigorous notions of function purity and immutability. Any program you develop will need impure functions to modify the state of JavaScript variables (named memory locations).

In general, it’s ideal to keep the impure elements of your programs distinct from the data processing, which is usually pure. Also, updating and maintaining your applications will be much easier if you confine impure elements to their particular functions.


### Advantages of impure functions

- Impure functions can use an in-place solution to reduce the space complexity.

- In impure functions, the state can be modified to use the parent variable and call for the function compiling.

# Let VS Var

- Variables declared by let are only available inside the block where they’re defined.
- Variables declared by var are available throughout the function in which they’re declared.
  


```js
function varScoping() {
  var x = 1;

  if (true) {
    var x = 2;
    console.log(x); // will print 2
  }

  console.log(x); // will print 2
}

function letScoping() {
  let x = 1;

  if (true) {
    let x = 2;
    console.log(x); // will print 2
  }

  console.log(x); // will print 1
}

```

   

# How do you redeclare variables in switch block without an error

If you try to redeclare variables in a `switch block` then it will cause errors because there is only one block. For example, the below code block throws a syntax error as below,

```javascript
let counter = 1;
switch (x) {
  case 0:
    let name;
    break;  
    
  case 1:
    let name; // SyntaxError for redeclaration.
    break;
}
```

To avoid this error, you can create a nested block inside a case clause and create a new block scoped lexical environment.

```javascript
let counter = 1;
switch (x) {
  case 0: {
    let name;
    break;
  }
  case 1: {
    let name; // No SyntaxError for redeclaration.
    break;
  }
}
```

   

# What is memoization

Memoization in javascript is an optimization technique, to reduce the complexity of the application, runtime of the application, and proper utilization of resources (Time and Memory). The process consists of using an extra space (cache) for the reduction of expensive function calls (a function that recursively calls itself and it has some overlapping problem). By using memoization, we store the values that were calculated in the previously called subproblems. Then if the same subproblem is raised, we again use the stored value which reduces the time complexity as it removes the extra effort to calculate again and again for the same problem.
    

## How Does Memoization Work?

JavaScript Memoization mainly depends on two concepts:

- Closure
- High-order function

## Closure

The Closure is a combination of a function enclosed with its references to the state. A closure allows you access to an outer function's scope from an inner function. In javascript, at the time of function creation, the closure is generated.

## High Order Function

A higher-order function is a type of function that operates on other functions, they either take other functions as arguments or returns them.

## Importance of Memoization

- Memoization in javascript is an optimization technique that stores the results of function calls in a temporary data structure and then retrieves the results whenever the stored result is needed in the program. By doing this, the execution time is reduced and the CPU performance is increased

- Using Javascript Memoization we can reduce the time complexity of an application and by which the response time of the webpage will decreases (for eg. API call)


## When to Use Memoization?

- When the function is calling itself. i.e. for the recursive functions.
- When the function is pure (a function that returns the same value every time it is called). As if the value is different in each function call, then there will not be any use in storing such value. So, we can't use memoization in javascript when the function is impure.
- When the function is very complex in time(Heavy computation function). In this case, storing the results in a cache will increase the performance by reducing the time complexity, as re-computation for functions will not be performed.

# What is Hoisting

Hoisting is a JavaScript mechanism where variables, function declarations and classes are moved to the top of their scope before code execution. Remember that JavaScript only hoists declarations, not initialisation.
   

```javascript
console.log(message); //output : undefined
var message = "The variable Has been hoisted";
```

The above code looks like as below to the interpreter,

```javascript
var message;
console.log(message);
message = "The variable Has been hoisted";
```

In the same fashion, function declarations are hoisted too

```javascript
message("Good morning"); //Good morning

 function message(name) {
   console.log(name);
 }
 ```

This hoisting makes functions to be safely used in code before they are declared.

   

   

# What are closures

In javascript closures are basically like function that remembers and access variables from their parent scope even after the parent function has actually finished execution.

It's like a function that carries a piece of past with it wherever it goes.

```js

function outerFunction() {
  var outerVariable = 'Hello';

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

var closureExample = outerFunction();
closureExample(); // Output: Hello


```

In this example, innerFunction is defined inside outerFunction and has access to the outerVariable even after outerFunction has completed. When we invoke outerFunction and assign its return value to closureExample, we essentially create a closure. When we later call closureExample(), it still has access to the outerVariable and prints "Hello".
   

   

# What is a service worker

A Service worker is basically a script (JavaScript file) that runs in the background, separate from a web page and provides features that don't need a web page or user interaction. Some of the major features of service workers are Rich offline experiences(offline first web application development), periodic background syncs, push notifications, intercept and handle network requests and programmatically managing a cache of responses.

   

# How do you manipulate DOM using a service worker

Service worker can't access the DOM directly. But it can communicate with the pages it controls by responding to messages sent via the `postMessage` interface, and those pages can manipulate the DOM.

   

# How do you reuse information across service worker restarts

The problem with service worker is that it gets terminated when not in use, and restarted when it's next needed, so you cannot rely on global state within a service worker's `onfetch` and `onmessage` handlers. In this case, service workers will have access to IndexedDB API in order to persist and reuse across restarts.