## Topics Covered
Closure, Function returning function, Lexical Environment and Execution Context behaviour with closure.
## What I Learned
Lexical Environment is combination of variable environment plus reference to its parent/outer lexical environment.
Closure -  function along with its lexical scope.
## Things That Confused Me
So there are closures that are formed even when Execution context  of parent is alive (Example 1)
And then there are closures that are formed when Execution context of parent is all together popped from stack, still it preserved the lexical environment.- Ex2

So can we say closure is the funtion along with its lexical environment. It is something that is preserved for the time where function will be called and not the time when it is defined. (there is polished version of this statement in 30 seconds revision).
## Interview Questions
- What is closure?
## My Own Explanation

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

Since Y preserved the lexical environment ( which is created based on where the function is difined before the execution of code.), Though x ended and its EC is also removed from the call stack before reaching the line where we are calling temp(), yet  will preserve lexical env and will print 1000 (not 90).
++++++++++++++++++++++++++++++++
## Interview Discussion

## Revision in 30 Seconds
-Lexical Environment is combination of variable environment plus reference to its parent/outer lexical environment.
-A function forms a closure with its lexical environment when the function is created. If it references variables from that lexical environment, it can access them whenever it executes.


