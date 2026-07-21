Topics Covered - **Execution Context, Single Thread syncronous JS, Memory (JS variable env), Code (Thread of Execution)**



## What I Learned
Execution Context, Single Thread Syncronous JS, Parts in EC - Memory/Code

## Things That Confused Me
Got bit confused on how let and const will be initialized in phase 1 of memory allocation.

## Interview Questions
What is Execution Context?
How a program runs in background in JavaScript?
Is javaScript Multi-threaded or Single-threaded? What is difference in 2 of them?
We say JS is syncronous language still we have things like AJAX which defined asyncronous nature. What's the catch here?

## My Own Explanation
So every JS program when runs on a machine, it creates an execution context. That is everything runs inside it. Execution context can be seen as large container divided into 2 parts - Memory part( AKA JS variable environment ) and then Code part (AKA Thread of execution).

It happens in 2 phases, first is memory allocation or initiation part. In this all variables and functions are intiailised in Memory part (variables are intialized with Undefined(I guess there is some different value for let and const) and then functions are put as is (whole function definition). Then next phase is code execution phase where js engine executes code line by line since js is a single threaded (meaning one line of code at time can be executed) Syncronous language (It follows order of execution).

## Code Examples

var a=10
function test(){
  var a=20
}
var t = test();

a,test and t will be first initialized in memory section and then code will start executing line by line. (Note that a and t will be initialized with undefined, whereas for test, you'll see whole function definition).
