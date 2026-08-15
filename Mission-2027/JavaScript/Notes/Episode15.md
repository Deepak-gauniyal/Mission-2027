## Topics Covered
Call Stack, JS Engine is one part of Browser, Web APIs, Event Loop and callback Queue( aka Task Queue). Registring a callback and attaching an event to it. Fetch() and micro Task queue. Starvation of callback queue.
## What I Learned
JS engine executes whatever comes into call stack quickly without waiting for anything. meaning there is no timer or anything attached to it. So if we want to run something after delay of let say 10 second then how it will work?

JS Engine is just one part of browser, Browser carries many functionalities in itself like local storage, timers, URLs, location, bluetooth etc.. It can even make connection to outer world like connecting to Netflix and can beautifully then show that on UI as well. So browsers are superpowerful.

Not to make JS Engine use all these browser functionalites, we get Web APIs.  Example of Web APis are setTimeout,DOM apis(document.getElement...),fetch, local storage, console, locations etc. So yesss even console.log that you are writing is part of browser and not Javascript. setTimeout is part of browser API and not JS. Done be sad. 
Browser gives this power to JS Engine to use all these web APIs to call these apis.
So Browser gives this access through a global object and that global object is window. If you want to use setTimeout you'll do something like
window.setTimeout()
or you can use it without window keyword also.

Callback Queue is the queue where call back functions that are ready for execution waits. 
Event Loop is the middle layer between calllback queue and Call stack. Basically it monitors call stack if it can take call backfunction and then if available it puts it (function waiting at callback queue) into call stack and execute it.

Fecth() is web APi used to make connections to external network.

fetch('hppts url').then(function cb1(){ console.log(result)});

Here a this call back function cb1 will be registered in web API and will wait for response from external system.(Promises) Once it recieves response ( Does it moves to callback queue?) - the answer is no. Similar to callback queue we have microtask queue.

Microtask queue is somewaht similar to callback queue but it has higher priority.

Event loop continously moniteor call stack, one call stack is empty, it will first prioritize functions in microtask queue and then to callback queue.

What are microstastks in js - call back functions that comes through promises as well as mutation observers (that observes any change in DOM tree).

Starvation of callback Queue - So there are chances that microstask creates another micro task and then new mictotask creates another one and will go on. In this scenatio the call back function waiting in call back queue will never get chance to execute ( as it has lower priority). This is know as starvation of call back queue. We can read more about it for sure.

Next will cover JS Engine Arvhitecture.

## Things That Confused Me
Why we need callback queue . Why event loop cannot direclty take registered call back?
## Interview Questions
 - What are microtasks in JS.
## My Own Explanation
Same as What I learned
## Code Examples
  setTimeout(fucntion xyz(){console.log('hello')},5000)
  at this point function xyz will be registered in web APi and a timer will start of 5000ms. Main thread of execution will continue its work. When timer triggers, it will push xyz to call queue. Event loop will keep monitoring Call stack, if its empty then it will pop xyz from call back queue and push to call stack for execution.

  #######################

  document.getElementById('btn122').addEventListener('click',function cb1(){console.log('clicked')});

  In above scenario, browser will register callback function in webAPI and will attach event to it. So whenever user clicks on button, it will take that function and move it to callback queue. Then Event loop is responsible for further action.

  ############################

 fetch('hppts url').then(function cb2(){ console.log(result)});

 fetch return a promise and when promise is resolved, cb2 will be pushed into microtask queue. Microtask queue has higher priority then callback queue, so even if both queues have some functions ready to executed, Event loop will prioritze functions in microtask queue first.
## Interview Discussion
- Will do this later
## Revision in 30 Seconds
JS Engine is one part of Web Browser responsible for executing JS code using call stack and execution contexts. Apart from JS engine , browser has many features that can be used in JS code using web Apis like setTimeout,DOM, fetch, console etc.
Whenever a callback is registered in Web API, it waits there and then if it satisfies some condition (like timer triggering in case of setTieout), it will be either pushed to callback queue or microtask queue (higher priority - mainly for promises and mutation observers).
Event loop is mediater between javascript engine and callback + microtask queue. It continuously monitor call stack, if call stack is empty, it will check if anything is ready to be executed in microtask queue, if yes it will push it into call stack and execute. Once microtask queue is empty then it will check in call back queue.
