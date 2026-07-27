## Topics Covered
Closure, Function returning function, Lexical Environment and Execution Context behaviour with closure.
## What I Learned
Lexical Environment is combination of variable environment plus reference to its parent/outer lexical environment.
Closure -  function bundled with its lexical environment forms closure.
## Things That Confused Me
So there are closures that are formed even when Execution context  of parent is alive (Example 1)
And then there are closures that are formed when Execution context of parent is all together popped from stack, still it preserved the lexical environment.- Ex2

So can we say closure is the funtion along with its lexical environment. It is something that is preserved for the time where function will be called and not the time when it is defined. (there is polished version of this statement in 30 seconds revision).

Introduction of Places where closure is used and how useful it is:
- Module design patterns, currying, functions like once, memoise, maintaining state in async world, setTimeouts, iterators and many more.
## Interview Questions
- What is closure?
- What is the difference between Lexical Scope and Closure? - Lexical Scope determines where a function looks for variables based on where it was defined.
Closure is the mechanism by which a function retains access to that lexical environment.
## My Own Explanation
_ Same as what I learned and things that confused me collaborated.
## Code Examples
function x(){
  var t=0;
  function y(){
    console.log(t);
  }
  y();
}
x();

Above is simplest example of closure. You can imaging flow here as GEC(func:x | LE(global parent which points to null)) -> FEC_X(t:0,func:y | OuterLE(Global)) --> FEC_Y (Since in vairable env of Y there is no t, it will look for it in its lexical environment, that is its outer lexical env, since t is there it will print 0).

Here y forms a closure ( because it is referring to its outer lexical environmet for some values. It will preserve it does not matter whether outer EC is removed from call stack or not). In above example outer EC was still there in Call stack, so it is looking like nothing special happened. But in example below you'll see a change.
Although this is a closure, the outer Execution Context is still active, so JavaScript doesn't need to preserve anything beyond what already exists.
++++++++++++++++++++++++++++++
var a=90;
function x(){
  var a=1000;
  function y(){
    console.log(a);
  }
  return y;
}
var temp=x();
temp();

Since Y preserved the lexical environment ( which is created based on where the function is difined before the execution of code.),Although the Execution Context of x() has been removed from the call stack, the lexical environment referenced by y() remains available through the closure. before reaching the line where we are calling temp(), yet  will preserve lexical env and will print 1000 (not 90).
++++++++++++++++++++++++++++++++
## Interview Discussion
- Will do it at the end of course.
## Revision in 30 Seconds
-Lexical Environment = Variable Environment + Reference to the parent's Lexical Environment.

-Closure = A function bundled together with the lexical environment in which it was created. Because of this, the function can access variables from that lexical environment whenever it executes, even if the outer function has already finished.
-The function carries a reference to its lexical environment. If the outer Execution Context has already been removed from the call stack, JavaScript keeps the required lexical environment alive so the function can still access those variables.

