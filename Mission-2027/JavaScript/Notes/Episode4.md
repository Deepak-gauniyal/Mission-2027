## Topics Covered
Funtion Execution Context, Call stack and example on web browser, local variable reference
## What I Learned
 So in this video we continued understading function and how they are executed . We took example of call stack and hoisting and saw how for different execution contexts a separate memory is alloted and how that Separate FEC can be seen as small separate part of code independent of anything outside (Though it partially true).
## Things That Confused Me
 When to use lexical scope or lexical environment and when to use Execution context or memory there.
## Interview Questions
  Explain Hoisting.
  If a variable a is present in local scope as well as global scope, What value will function consider?
  If variable is present in global scope but not declared or defined in local scope and function tries to print it. What then?
  
## My Own Explanation

## Code Examples
var a = 10;
f1(); // 20
f2(); // 30
console.log(a) //10

function f1(){
  var a=20;
  console.log(a)
}

function f2(){
  var a=30;
  console.log(a)
}

## Interview Discussion

That is something will add after completing drill

## Revision in 30 Seconds
With Given example, you can test your knowledge on Execution context, gloabal and local scope and what gets prioritized when running a function.
