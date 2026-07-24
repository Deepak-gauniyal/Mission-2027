## Topics Covered
Lexical Environment,Scope Chain
## What I Learned
Lexical Environment - It is local memory plus Lexical environment of its lexical parent (Parent in which that function or block is defined). 
Scope chain - A variable when trying to get its value, it will first check in local memory, if not found then it will check in Lexical environment of parent. If in Lexecial Environment of parent local storage it is not there, then it will check in Lexical environment of parent (that is its grandparent). This process will keep on unitl we find that variable value or we reach End of code. This Chain of lexical environment is called scope chain. Basically chain of LE till which one particular variable can be accessed. if a varaible a used in function A can be accessed in function D, means a is in scope of D.
## Things That Confused Me
When we say Lexical Environment, Scope and Execution context memory part difference.
## Interview Questions
- What is Lexical Environment how it is different from Execution Context.
- What is scope of a variable or function.
- Can I see Lexical Environment in browser console?
  
## My Own Explanation
Same as 'What I learned' section
## Code Examples
function A(){
  B();
  function B(){
    console.log(c);
  }
}
var c=101;
A();

Here it will print value as 101 becuase call stack will look like --> GEC->FEC(A)->FEC(B)
Since var c is not present in local memory of B it will look for it in its lexical environment (that is local memory of A and its lexical env)
In local memory of A, again var c is not there , so it will look into A's lexical enviroment (that is local memory of GEC and its lexical env [null])
Since c is present in local memory of GEC. It will take that value of c and print
## Interview Discussion
- Will keep this for end.
## Revision in 30 Seconds

