## Topics Covered
 Let and Const , Temporal Dead zone
## What I Learned
Let and const declarations are hoisted but they remain in temporal dead zone (Separate memory) till the time the line which is assigning value to it gets executed.
IF you try to access let and const variables before initialization it will throw reference error - cannot access variable before initialization.
In memory allocation phase, let and const are allocated memory(they are hoisted) in some separate memory space.

LEt and const variable when memory is allocated to them, till the time a value is assigned to it- They remain in TDZ. Variables in TDZ cannot be accessed.
Also let and const are also not attached to window(global) object. As they are maintained in separate memory space. 
let is little more stricter than var. Let does not allow redeclaration also meaning  :
let a=10;
let a=100; // This will throw **syntax error**- Identifier has already been declare

const is very much similar to let -- Its just that it wont allow value reassignment. Also a value needs to be assign upfront to const. That is you cannot leave const type of variables unitialized.
const a; //** SyntaxError** - Missing initialization in the const declaration.
a=10;

++++++++++++++++++++++++
const a=10
a=20 // **TypeError** - Assignment to constant variable

Const and let are highly recommended to be used.
TDZ can make things worse sometimes, So recommended practice is to define and declare variables at the top of code,s o when you go to use them they wont throw unexpected errors.
Let and const have block level scope

## Things That Confused Me
let and const are allocated in different memory then var variables?Even after initialization?
Temporal dead zone is a memory space, or its just a term?

## Interview Questions
Difference between let and const.
What is TDZ?
After assignment do let and const move to global memory scope?

  
## My Own Explanation
- IT is same as What I learned section
## Code Examples

const x;// Error
const a = 10
a=20 // Error
let b = 10
let b = 90 // Error
var b=100 // Error


## Interview Discussion
- Will keep it for end of topic
## Revision in 30 Seconds

- Temporal Dead Zone (TDZ) is the area where let and const declared variable remains from memory allocation phase till the time they are initialized.
- Let kind of variable does not allow redeclaration, though they can be assigned multiple times
- const variables does not allow redeclaration plus reassignment. Also they must be assigned value when we are declaring them.
- Both of them are hoisted, but are not availble to use before assignment as they remain in TDZ. 
