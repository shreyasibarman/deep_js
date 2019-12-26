# Function Scope (IIFE)



IIFE stands for **Immediately invoked function expressions**.

Used when we need to _invoke_ a function instead of _declare_ it.

Used because function declarations cant be invoked directly.

Line 3 is not executed as a function declaration (hence not processed during compile time to assign to a scope) because the first word is not _function_ , it includes parenthesis instead.

IIFEs can be made anonymously (bad practice) but it’s better to give it a name. It can be used to make sure a variable only gets assigned once so as to avoid _name collision_.



<img src="deepimages2/4.jpeg" height="300px" width="400px" >
