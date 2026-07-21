## What I Learned
Global Execution Context, Local Execution Context, Call Stack (AKA Execution stack, process stack etc.)

## Things That Confused Me
how let and const are initilized in memory allocation stage.

## Interview Questions
Explain JS runtime scenario with examples.
Difference between global Execution context and local execution context.
What is call Stack, which one thing is there at the end of stack?
Difference between arguments and parameters?

## My Own Explanation
In this we saw one example on how exactly flow works when we run a JS program. As soon as we run one Execution context gets created (We call it Global Execution context). Then as we discussed ealier it will happen in 2 phases - 1 is memory initiation and 2nd is code execution.

One interesting thing covered here was when a function is called in global execution context , it creates its own local execution context inside global EC. Once function is finished, we'll start pointing back to the parent EC, which in above example case was GEC.

Then comes the term EXECUTION STACK. So when we run program, GEC is pushed inside EXECUTION stack, then when a function let say f1 is called, A fresh execution context for F1 is created, so we'll push this F1 execution to stack. Once F1 is finished, we pop it out of Execution stack, and once GEC is also finishes we pop it out of Execution stack as well and that's where program ends.

Interestingly you'll understand below example:

console.log(a)
var a=10
function test(){
  console.log(a)
  var a=20
  console.log(a)
}
console.log(a)
test();
console .log(a)


**Here output would be - undefined, 10,undefined,20,10**

the third one is undefined becuase when function was called, it created its own execution stack, That execution stack was having its own variables and functions hoisted and top of its scope. That means a would be locally hosted in the execution stack of test(). So in this case it will refer its local scoped a instad of global 'a'. And also the changes you are did inside function is not going to hamper gloabal 'a'.

## Code Examples

Explained everything above. May attach one Flow chart here later on.
