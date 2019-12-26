# Dynamic Global Variables


Since line 4 is not a formal declaration, there will be no blue marble created during compilation,
however during execution of line 9, local will move up to global.

(how?) since it can’t find the variable _teacher_ in the present local scope, it will move to the upper scope and look for the same variable there and hence change it.

The global variable _teacher_ will change to “Suzy”.

Since _topic_ doesn’t exist in global scope, dynamic global variable _topic_ will be created (known as "auto-global") during run time.

<img src="deepimages/2.jpeg" width="400px" height="300px">

#### Note :
Creating auto-globals is a bad practice as it happens in run time can behave in an unpredictable manner: always declare your global variables, avoid making auto-globals.




