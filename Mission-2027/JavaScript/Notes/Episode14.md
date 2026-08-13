## Topics Covered
- First-Class Functions
- Callback Functions
- Synchronous vs Asynchronous JavaScript
- setTimeout
- Blocking the Main Thread
- Event Listeners
- Closures with Event Listeners
- Garbage Collection
- removeEventListener
- Event Listener and Memory Management
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
1. How do we remove an event listener from a button when we don't know when the user will click?
        We don't remove it based on when the user will click.
        We remove it when the listener is no longer needed.
        For example, if a component is destroyed:
        
        Component created
              ↓
        Add listener
              ↓
        User interacts
              ↓
        Component destroyed
              ↓
        Remove listener
        
        This concept becomes especially important when we learn React's useEffect cleanup.

2. Why not use a global variable for a counter?

        We could:
        let cnt = 0;
        function increment() {
            cnt++;
        }
        But now the variable is accessible to other code within its scope and can potentially be modified unintentionally.
        
        With closure:
        
        function counter() {
            let cnt = 0;
            return function () {
                cnt++;
                console.log(cnt);
            };
        }
        
        cnt is not directly accessible from outside.
        Therefore closure can provide:
        Persistent state + controlled access to that state.
## Interview Questions
- Explain Event listener with an example.
- What happens when there are 100 of events. Do they make program slow? how to solve it?
- Why using global variable is not a first choice for counter though it is easier then making a closure out of it.
- What is a callback function?
- What is the difference between a first-class function and a callback function?
- Is every callback function asynchronous?
- Give an example of a synchronous callback.
- How does setTimeout work at a high level?
- Does setTimeout stay on the call stack until the timer expires?
- What does blocking the main thread mean?
- What is an event listener?
- How does an event listener use a callback?
- How does closure work with event listeners?
- Why does a variable remain accessible after the outer function finishes?
- What is garbage collection?
- When can a closure prevent something from being garbage collected?
- Why should we remove event listeners?
- Why does removeEventListener() require the same function reference?
- Do 100 event listeners automatically make an application slow?
- What is event delegation?
- Why would you prefer a closure over a global variable for maintaining state?
## My Own Explanation
- JavaScript functions are first-class values, which means they can be assigned to variables, passed as arguments and returned from other functions.
- When a function is passed to another function and is intended to be called by it, we call it a callback function.
- Callbacks themselves are not necessarily asynchronous. They can execute synchronously as well. However, asynchronous APIs such as setTimeout can execute their callbacks later.
- JavaScript is single-threaded and has a main call stack, so long-running synchronous code can block the main thread and make the application unresponsive.
- Event listeners allow JavaScript to respond to events such as clicks, input, mouse movements, etc. We provide a callback function which gets executed when the event occurs.
- Closures become useful with event listeners when the callback needs to remember some state from its outer environment.
- For example, a counter inside an outer function can continue to be accessed and updated every time a button is clicked.
- Event listeners should be removed when they are no longer needed. removeEventListener() requires the same function reference that was used while registering the listener.
## Code Examples
**_1. Callback Function_**
function x(callback) {
    console.log("x");
    callback();
}

x(function () {
    console.log("y");
});

Output: x
y

**_2. setTimeout_**
console.log("A");

setTimeout(function callbackEx() {
    console.log("B");
}, 1000);

console.log("C");

Output: A
C
B

setTimeout() doesn't block JavaScript for one second.

**_3. Callback + Asynchronous API_**
function x(callback) {
    console.log("x");
    callback();
}

setTimeout(function () {
    console.log("z");
}, 1000);

x(function () {
    console.log("y");
});

Output: x
y
z

x() and its callback execute synchronously.
The setTimeout callback executes later.

**_4. Closure with Event Listener_**
function attachEventListener() {

    let cnt = 0;

    document.getElementById("someId")
        .addEventListener("click", function () {
            console.log("Button clicked", ++cnt);
        });
}

The callback maintains access to cnt through closure.

**_5. Removing an Event Listener_**
function handleClick() {
    console.log("Clicked");
}

button.addEventListener("click", handleClick);

// Later
button.removeEventListener("click", handleClick);

Same function reference is used for both operations.

**_6. Incorrect removeEventListener_**
button.addEventListener("click", function () {
    console.log("Clicked");
});

button.removeEventListener("click", function () {
    console.log("Clicked");
});

This doesn't remove the original listener because the two anonymous functions are different function objects.
########################################################################


## Interview Discussion
**_Callback vs First-Class Function_**

First-class function describes what JavaScript allows us to do with functions.
Callback describes how a particular function is being used.

function greet() {
    console.log("Hello");
}
// greet is a function value.

someFunction(greet);
// Now greet is being used as a callback if someFunction invokes it.

**_Callback vs Asynchronous_**

Don't say:
"Callbacks make JavaScript asynchronous."
Instead:
Callbacks can be used in both synchronous and asynchronous operations. APIs such as setTimeout and browser events can invoke callbacks asynchronously.

_**Event Listener + Closure**_

    The important relationship is:
    
    Event Listener
          ↓
    Callback Function
          ↓
    Callback uses outer variable
          ↓
    Closure
          ↓
    Outer state remains accessible

This is why a counter can maintain its value across multiple button clicks.

_**Event Listener + Garbage Collection**_

An event listener can maintain references to its callback, and the callback may maintain references to variables through its closure.
As long as those objects remain reachable, garbage collection cannot reclaim them.

When the listener and related objects are no longer reachable, they can eventually become eligible for garbage collection.
## Revision in 30 Seconds
JavaScript functions are first-class values, so they can be assigned, passed and returned. A callback is a function passed to another function so that it can be invoked by it. A callback itself is not necessarily asynchronous; asynchronous APIs such as setTimeout and browser events can invoke callbacks later. Event listeners register callbacks that execute when specific events (such as clicks and input) occur. If an event callback uses variables from its outer scope, it forms a closure and can retain access to that state even after the outer function finishes. Long-running synchronous JavaScript can block the main thread. Event listeners should be cleaned up when they are no longer needed, and removeEventListener() requires the same function reference used when registering the listener.

Three things I should remember
1. Callback ≠ Asynchronous
   Callback + asynchronous API(Ex settimeout) → can participate in asynchronous behavior.
2. setTimeout doesn't stay on the call stack while waiting. The setTimeout API is handled by the host environment (browser).
3. removeEventListener() needs the same function reference.
