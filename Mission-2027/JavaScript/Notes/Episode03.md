## Topics Covered

Hoisting in JS, Different type of function definition and its impact in hoisting, Call stack real example.

## What I Learned

Concept of hoisting( When a JS program runs, it creates the gloabal execution context, in that first phase is memory allocation phase where memory gets alloted to variables and functions. var type variables are initialized with undefined where as function declared in specific format (not arrow functions or var a=function(){}) are put into memory as is with full definition. Then when phase 2 starts that is code execution part, we are able to use function and variables even before they are declared or assigned some value in the code. This phenomeone is called as hoisting (people generally call it as function and variable declarations are moved to the top of code, which is not exactly true. I already explained memory allocation phase above).

var a = function(){console.log('Hello');};
var a = () => {console.log('Hello');};

If user declare function in above 2 formats, then in memory allocation phase, JS treats them as variables and initialize them as undefined. In this case in your code if you try to call them before declaration , it will throw an error saying a is not a function. Whereas if you define it like

function a(){console.log('Hello');}

In Above case it will print Hello, since not it will treat it as function instead of variable.

We also saw example of call stack and how it works in browser debugging tools.
## Things That Confused Me
Nothing in this video.
## Interview Questions
What is Hoisting in JS?
I declared a function but when trying to call it in first line of code it is giving error as if it is not a function. What could be the reasons?
What is difference between undefined and not defined. Explain with an example.
## My Own Explanation
In Execution context, first phase is always memory allocation phase, in this phase all variables and functions gets there respective memory space in the lexical scope. Once program start executing code, it will refer this memory for any value. So basically we have allocated memory for var and fucntions before code execution where they are intialized as well (not for let and const). This is known as Hoisting. Now in our code if very first line wants to access these var or function, it can access without any error.

But in code if you try to access something to which memory is not allocated in memory phase, for eg you try to access and log variable 'b', which is no where defined or declared in code, hence not present in memory. In that case you get error as variable b is not defined. If 'b' would have been defined anywhere in the code, then you would be getting 'undefined'. So here lies difference between not defined and undefined.

## Code Examples
console.log(a) // undefined
console.log(greet()); // Hello Deepak
console.log(greet); // function greet(){console.log('Hello Deepak')}
console.log(treat); // undefined
console.log(treat()); // Error - treat is not a function.
console.log(b); // b is not defined

var a = 10
function greet(){
  console.log('Hello Deepak');
}

var treat = function(){
  console.log('This is Treat');
}

## Interview Discussion

## Revision in 30 Seconds
My own Explanation covers same thing.
