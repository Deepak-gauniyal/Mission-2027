## Topics Covered
Shadowing, block scope and difference for var, let and const
## What I Learned
Shadowing - If a same variable is declared in different lexical environment, The one closed to the block where it is getting used takes priority and rest are shadowed.
Block - Block is also called compound statement. So basically when we want to group some statements- we keep it inside a block{}.
Block level scope behaves very differently for var vs let and const. 


## Things That Confused Me
block level scope behaviour of let and var.
Do block creates separate execution context?
## Interview Questions
Why let and cosnt are called block scoped.
Wht is shadowing.
## My Own Explanation
- Same as what i learned.
## Code Examples
var a=100
console.log(a); //100
{
  var a=10;
}
console.log(a); //10
var declare in block remains in global scope, so instead of defining variable in lexical environment of block, It will refer to the variable defined in gloabal scope.
+++++++++++++++++++++++++++++++++++++++++

let a=100
console.log(a);
{
  let a=10
  console.log(a); //10
}
console.log(a); //100

Thats why we see statmeent like let and const have block level scope. Basically when let and const kind of variables are declared inside block, Separate memory is allocated to them in block scope (or  we can say lexical environment). Once block is over, its lexical environment will be destroyed and so as its local memory of a. Thats why in next line it printed 100.

+++++++++++++++++++++++++++++++++++++++++++++++++++

var a=100
{
 let a =1000
}
console.log(a) //100 Since var a is in global memory space and let a is in block scope, so 2 different references.
+++++++++++++++++++++++++++++++++++++++++++++++++

let a=100
{
  var a=10
}
console.log(a)
Error - Let kind of variale cannot be redeclared. Because both these memory will lie in same space, hence it will not allow
## Interview Discussion
 - Will keep it for end.
## Revision in 30 Seconds
- Shadowing - if one variable gets declared in multiple places, The one close to where it is used gests priority and other gets shadowed.
- Var even if declared in block gets global memory. hence it referes to global memory and any changes happenign inside block reflects in global scope as well. 
