## Topics Covered
First Class Functions, Anonymous function, Function statement vs Function expression vs Function declaration, Anonymous functions, named function expression,param vs arguments, first class function, arrow function
## What I Learned
// _Function Statement_ it is also known as function Declaration- 
function funName1(){
  console.log(10);
}
// _Function Expression_
var funName2 = function(){
  console.log(10);
}
The difference here between above 2 lies with hoisting. During the memory creation phase, funName1 will be provided memory and whole function statement is stored as value. Where as in case of funName2 in memory creation phase, memory will be assigned to funName2 and it will be initialized as undefined. So it will treat it as any other var variable. So if you try to call it before assignment (Shown in example) it will throw error.
The variable declaration is hoisted, but the function value is assigned only when execution reaches the assignment.


//_Anonymous Functions_

function without name is called anonymous function.
function(){} // If we direclty write this it will throw error that function statments require a function name. So where we use anonymous function then?
An anonymous function is used, when we want to use functions as a value, typically passing them as argument to another function or you can assign them to another variable (basically function expression in above example).

// _Named Function Expression _
An function expression with function name is known as Named function expression.
var funName2 = function xyz(){
  console.log(10);
}
 There is edge case here, if you try to call xyz(); in global scope it will throw reference error as xyz is not created in global memory. See example 2 for more details.

 // _Parameters and Arguments_
 function a(param1,param2){ // baiscally parameters are local variables to function and cannot be used outside function
   console.log(param1,param2);
 }

 a(10,20) // here 10 and 20 are arguments that is the value we passed inside function

 
 Parameters are the local variables defined in a function's parameter list; arguments are the actual values supplied when the function is called.

 // _First Class Functions_

 We can pass function inside another function as arguments, We can return a function from a function. The ability of a function to be used as values, passed to other functions and returning them from another function is known as first class functions. We may need exact definition to it.

 A language treats functions as first-class citizens when functions can be treated like other values—assigned to variables, passed as arguments, returned from functions, and stored in data structures.


 because of this function are also called _first class citizen._

 // _Arrow Functions_

 These are introduced as part of ES6.
 Will cover separately in later sections.

## Things That Confused Me
Doesn't get the purpose of named function, why we need to do this. recurssion? - Yes guess is correct, with named function, you do not have to rely on outer function for recursion, you can simply use named part. 
## Interview Questions

## My Own Explanation

## Code Examples
a(); //10
function a(){
  console.log(10);
}

b(); // b is not a function 
var b = function(){
  console.log(11);
}

#########################################
var b = function xyz(){
  console.log(10);
}
b(); // 10
xyz(); // Reference Error : xyz is not defined.

var b = function xyz(){
  console.log(xyz);
}
b(); // definition of function xyz.

Inside function we can refer it, but in outer environment we cannot. Bit confusing but thats how things are working.
## Interview Discussion

## Revision in 30 Seconds

Function Declaration: Function is created during the memory creation phase, so it can be called before its declaration.

Function Expression: Function is assigned to a variable during code execution. With var, the variable is initially undefined, so calling it before assignment gives a TypeError.

Anonymous Function: A function without a name, commonly used when functions are treated as values.

Named Function Expression: A function expression with an internal name, useful particularly for recursion and debugging.

Parameters: Variables defined in the function declaration. Arguments: Actual values passed during invocation.

First-class functions: Functions can be treated like values—assigned, passed, returned, and stored.
