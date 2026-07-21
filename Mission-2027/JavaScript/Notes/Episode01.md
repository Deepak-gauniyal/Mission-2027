Topics Covered - **Execution Context, Single Thread Asyncronous JS, Memory (JS variable env), Code (Thread of Execution)**

So every JS program when runs on a machine, it creates an execution context. That is everything runs inside it. Execution context can be seen as large container divided into 2 parts - Memory part( AKA JS variable environment ) and then Code part (AKA Thread of execution).

It happens in 2 phases, first is memory allocation or initiation part. In this all variables and functions are intiailised in Memory part (variables are intialized with Undefined(I guess there is some different value for let and const) and then functions are put as is (whole function definition). Then next phase is code execution phase where js engine executes code line by line since js is a single threaded (meaning one line of code at time can be executed) Syncronous language (It follows order of execution).
