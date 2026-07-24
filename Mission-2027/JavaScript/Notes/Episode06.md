## Topics Covered
undefined vs not defined, JS is loosly typed 
## What I Learned
undefined - Special keyword, gets assigned to var variables at the time of memory allocation not defined - Something to which memory is not allocated. We should not explicitely assign undefined to any variable (it will work but its not a best practice). JS is loosly typed or weakly typed language (meaning a variable initially assigned string value can take up Number value in later part of code without any error). 
## Things That Confused Me
Akshay said that undefined meaning a variable is allocated memory in the program. But so as let and const gets the memory allocated. Also when we do window.x (and suppose x is declared inside function A,so why we get undefined, though that x is not present in window object, Why it cant be that reference error?). 
## Interview Questions
Why JS is called loosly typed langauge? difference between not defined and undefined? If you try to access a property of window objec that does not exist - why it gives undefined instead of throwing reference error? 
## My Own Explanation
What I learned section covers it all. 
## Code Examples
var a;
console.log(a) // undefined
console.log(b) //Reference Error b is not defined. 
## Interview Discussion
Will keep it for end of the course. 
## Revision in 30 Seconds
undefined is special value that gets assigned to variables declared with var in memory allocation phase. If there is any variable we try to use to which memory is not allocated, there we get not defined error.
