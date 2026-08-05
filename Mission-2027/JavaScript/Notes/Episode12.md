## Topics Covered
Closure JS Questions
## What I Learned
Edge cases of closure. How closure can solve a problem where we use var in loops with setTimeout.
## Things That Confused Me
Nothing as of now.
## Interview Questions
- What is a closure in JS?
- Can you give example of closure?
- use of double parenthesis in JS ()()?
- Are Function parameter closed over?
- Relation of Scope Chain and Closures.
- Conflicting name global variables in JS
- Advantages of closure.
- Data Hiding and Encapsulation in Closures.
- function Instructor in JS.
- Disadvantages of Closure.
- What is the garbage collector?
- How closure and garbage collector are related to each other.
## My Own Explanation
 Nothing much to explain
## Code Examples
 Covered in interview discussion
## Interview Discussion
- A function along with its lexical environment forms a closure. Closure becomes more prominent when the execution context of the function in which it is defined is no longer available. Still the child function remembers variables and function from its lexical env.
- Give ex from episode 11.
- If there is a function and inside that another function is there and is getting returned. Through double parenthesis we can call the inner function. This is the way of writing. For eg:
  function outer(){
    function inner(){
    console.log('Hello');
  }
  return inner;
  }
  outer()(); // It will print Hello. We can say it is nested function call.
  //Above way is similar to
  let z = outer();
  z(); // It will print Hello

  - Yes and No both, the function with parameters when called with some argument, Function creates copy of those arguments into their parameters. That is if you change the parameter variable in parent program. It wont effect argument. So Smart way of saying is that arguments are closed over but not parameters. Even I am not sure about this.
  - If there are 4-5or even 6 nested functions, innermost will create closure with the lexical environment of immediate outer till outermost function. If some value is not found in first level, it will go to second then third and so on, hence creating scope chain.
  - Variables with conflicting name are prioritized based on where they are declared. Priority is always given to the one which was defined nearest to the function in which it is getting used.
  - Already Discussed.
  - Encapsulations is basically hiding data from other piece of code(Data Privacy). Basically if we want to control a data like who can access it that we can do through functions.
    var cnt=100;
    function incCnt(){
      cnt++;
    }
    console.log(cnt)

    //In above code anyone can update value of cnt, there is no data privacy. We can acheive it by enclosing it into a function like
    function counter(){
      var cnt=100;
      function incCnt(){
        cnt++;
      }
    }
    console.log(cnt); // It will throw error as not cnt can only be accessed through counter function. And if we want to update it like increment or decrement
    we can simply return it like **return incCnt();** at the end.
    Note : Whenever we call a function, a new object is created. Whateever we do in one object, does not change values in another. For eg:
    var t = f1();
    vat r = f1();
    if value in t is updated to 1000, and no change done in r. Then value in r will remain as 10. - This may be confusion in later point. I'll make it better when I'll refine notes.
  - Above way of returning function is not a good way for scaling the app. Instead we can use constructor function
    function construnctor(){
      var cnt=0;
      this.incCnt = function(){
        cnt++;
      }
      this.decCnt = function(){
        cnt--;
      }
    }
    var y = construnctor();
    y.incCnt();
    y.incCnt();
    y.decCnt();
    // So in above way we can create consturctor functions and you can see it is scalable, so its not just limited to increment, we can do decrement also.
    
- There can be overconsumption of memory. Those closed variables are not garbage collected. If not handled properly it can lead to memory leak, slowing browser.
- Garbage collector is a program that runs on browser and clears the memory which is no more in use. That is it frees up the memory.
- As we know in case of closure function along with its lexical env is preserved. That is variables and functions from outer env that might be used in inner functions, memory for them will also be preserved and not garbage collected. Modern browsers are now using smart techiniques and are only preserving variables or function that can actually be called in closure instead of saving all variables and functions from outer lexical environment.


## Revision in 30 Seconds
Can see these questions at the time of interview.
