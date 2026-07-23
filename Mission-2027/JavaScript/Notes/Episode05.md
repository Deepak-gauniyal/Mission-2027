## Topics Covered
Shortest Js program, window and this object, global and local scope.
## What I Learned
Shortest JS Program - So here if there is a js file without any line and if we try to run it, JS engine does it works - meaning it will create global execution context, Also it will create window object in browser.

Global execution Context - Variables and functions defined inside this are known as global variables and then if there are some variables that are defined inside function, those become local variables to that function.

JS engine creates a window object ( which has predefined function ) and in gloabl execution context window points to **this**. that means for example

var a=10
console.log(window.a);
console.log(this.a);
console.log(a)

All three of them will print same value that is 10.

So any variable/function you declare in global scope gets attached to window object as well.
## Things That Confused Me
this behaviour - I guess it might be covered in next scenario

## Interview Questions
What are global and local variables?
Difference between window object and this object?
Can you write shortest program in jS?
A variable t is defined inside function getName, The getName is defined in glaobal scope. what output will get when we do console.log(t) in global scope?Why?
  
## My Own Explanation
Whatever I wrote in What I learned section makes full sense here.
## Code Examples
var a=10
console.log(window.a);
console.log(this.a);
console.log(a)
function b(){
  var t=100;
}
console.log(window.t)

Output - 10,10,10, t is not defined (Since t is declared inside function b, it wont be available in global window object).
## Interview Discussion

This is something for end of the course.

## Revision in 30 Seconds

When you run a js code, any variable or function that is not inside any other function gets there memory allocated. This will reflect in window object, which JS engine creates as soon as a JS code starts running in browser. For Global scope - both window and this points to same object. The variales declared inside function are local to it, hence they are said to be in local scope of that particular function. 
