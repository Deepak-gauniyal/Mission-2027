## Topics Covered
Callback functions, Event Listeners, Blocking the main thread, Closure along with even listeners. Garbage collection and remove event listener
## What I Learned
Callback Functions - In Js function are first class citizens. meaning they can be used as a value and can be passed as an argument to another function. Such functions are known as callback functions. 
we know that JS is synchronous single threaded language. But this capability of call back functions help JS to do asynchronous operations.

setTimeout is the classic example.

Blocking main thread - Js is single threaded language, That is a single call stack. We have to be careful while writing the code that our code is not clocking that main thread. That is not taking its time indefinitely. Long-running synchronous JavaScript blocks the main thread because JavaScript executes code on the main thread and has a single call stack. While that work is executing, other JavaScript tasks and UI-related work may be delayed. (Infinite loop is typical example).

Event Listeners - In Javascript we have many event listeners like on click, on input, on hover etc. They listen to one particular statement and then call the callback function whehnever that event occurs. 

document.getElementById('someId').addEventListener('click',function(){
  console.log('button Clicked');
});

- Closure along with event listeners
  function attachEventListner(){
    cnt=0
    document.getElementById('someId').addEventListener('click',function(){
    console.log('button Clicked',++cnt);
    });
  }

  In above example event callback function creates closure with its outer environment and it remembers value of cnt. Akshay also showed same in event listener tab of developer tools. Something we can try at the end.

  event listeners are heavy, that means they take good amount of memory. If we have multiple events on our page it slows down the page because of so many closures and memory. That is why good practice is to removeEventListeners when not in use and with that garbage collection will happen. EVENT DELEGATION is better term whihc we'll study at later point in time.

  Next topic is going to be event loop.
## Things That Confused Me
In case of buttons, how can we remove eventListeners since we do not when someone is going to click them or not.
## Interview Questions
 Explain Event listener with an example.
 What happens when there are 100 of events. Do they make program slow? how to solve it?
 Why using global variable is not a first choice for counter though it is easier then making a closure out of it.
## My Own Explanation
Event Listeners are generally events that an end user can trigger like click, input, hover or the events that happen on browser like load, refresh etc. Event Listeners are important in understanding concept of event loops. 
Then callback functions, important in showing up async behavior of JS. 
## Code Examples
function x(y){

}
x(function y(){ // here function y is callback function, now its responsibility of x to call back that function in later point of time in the code.
//some code
});

##############################
setTimeout(function callbackEx(){
  console.log('z');
},1000);

function x(y){
  console.log('x');
  y();
}

x(function {
  console.log('y');
});
 Output - x,y,z
Above is typical example of Asynchronous behavior of JS. Here when setTimeout is called, it will store the callbackEx function at seprate storage and attach timer to it. Now JS wont wait for that setTimeout to trigger timer and then move to next line, instead it will move to next line and call function x(). See here though setTimeout was before x, still JS didnt wait on that line (this behavior is called async).
########################################################################


## Interview Discussion
- Will do it after course
## Revision in 30 Seconds
- A callback is a function that is passed to another function and is intended to be called by that function, either immediately or later.
- Callback ≠ asynchronous
  Callback + asynchronous API(Ex settimeout) → can participate in asynchronous behavior.
- the setTimeout API is handled by the host environment (browser).
- JavaScript functions are first-class values, so they can be assigned, passed and returned. A callback is a function passed to another function to be invoked by it. Callbacks themselves aren't asynchronous; asynchronous APIs such as setTimeout can invoke callbacks later. Event listeners register callbacks that execute when specific events occur. A callback can form a closure over variables from its outer scope, allowing state to persist between events. Long-running synchronous JavaScript blocks the main thread. Event listeners should be cleaned up when they are no longer needed, and the same function reference must be supplied to removeEventListener.
