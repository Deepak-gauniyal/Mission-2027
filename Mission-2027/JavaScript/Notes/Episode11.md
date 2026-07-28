## Topics Covered
Closure Example and setTimeout(). Let and var behavior in example.
## What I Learned
Closure can help in retaining values Ex2.
When setTimeout() is called, the JavaScript engine registers the callback with the browser (or the runtime environment such as Node.js). The browser starts a timer. Once the timer expires, the callback is placed into the Task Queue. When the Call Stack becomes empty, the Event Loop moves the callback from the Task Queue to the Call Stack for execution.
Closure carries the reference and not the value (that is if the value of variable is changed before the function call, it will print new value and not the old one). - Ex1
## Things That Confused Me
If there are 3 nested functions, why 2 of them are creating closure though only inner one is the one that is referencing something from global env?
Suppose in outer function there are 3 vars a,b,c but inner function only requires b. So in this case does in closure it will keep reference of whole outer LE(a,b,c) or does it keep reference of b only?
## Interview Questions
- if value of some variable is updated which is present in LE which is bundled with closure, does closure use new value or old one?
- where does setTimeout stored for given milli seconds ( Is there any queue ?). Can we see behaviour on browser?
- What is a call back function?
- Why does let fix the setTimeout loop problem?
## My Own Explanation
_ Same as what I learned and things that confused me collaborated.
## Code Examples
function a(){
  var t=98;
  function b(){
    console.log(t);
  }
  t=1000
  b();
}

Here output would be 1000 - Though when t was 98 , b function was defined, but as per definition closure carries reference to outer env and not value. So instead os storing t as 98, it will keep reference of t from outer env. hence when t value is updated, it will take update vale.
++++++++++++++++++++++++++++++
for (var i=1;i<6;i++){
  setTimeout(function(){
    console.log(i)
  },1000*i)
}
here idea is to print 1,2,3,4,5 each between duration of 1 seconds. 
But program will print 6,6,6,6,6 - Reason? - Because as mentioned earlier closure keeps reference and not value. Since before 1 second, whole for loop would have been executed and i's value would have become 6. That's the reason that after 1 second when first setTimeout callback function will be triggered, it will check for value of i, and will print 6.

This can be solved by using let, instead of var. As let is block scope. for each iteration it will create separate copy ( separate LE) so each setTimout function would be having separate references to i through separate LE. 

If interviewer ask to use var only and not let, then this problem can be solved using a wrapper closure function, something like.
for (var i=1;i<6;i++){
  function wrapper(x){
    setTimeout(function(){
      console.log(x)
    },1000*x)
  }
  wrapper(i);
}

In above way when we call wrapper, it will create copy of i and pass it to wrapper function. wrapper function will have the separate copy named as x in its Lexical environment or we can say variable environment. now any changes happening to i, as value of i is not referenced in x, it is copied in x.
++++++++++++++++++++++++++++++++
## Interview Discussion
- Will do it at the end of course.
## Revision in 30 Seconds
- better to use let when doing looping around closures( ex1).
- setTimeout when executes, put the call back function into separate memory space and attach timer to it. remaining code will keep on executing. **Once timer is fired, it will put that call back function back to call stack and it will be executed.** - This statement is wrong. Correct flow is
  Timer Expires --> task Queue --> Event Loop --> call stack.  That is callback isn't triggered immediately, instead it becomes eligible to run.

Polished version
- A closure captures references to variables in its lexical environment, not snapshots of their values.
- The classic var + setTimeout loop prints 6 repeatedly because all callbacks share the same i.
- let creates a new binding for each loop iteration, so each callback closes over a different variable.
- setTimeout schedules callbacks through the runtime environment; after the timer expires, the callback waits in the Task Queue until the Event Loop moves it to the Call Stack.

