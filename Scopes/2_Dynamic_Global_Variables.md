# Dynamic Global Variables


Since line 4 is not a formal declaration, there will be no blue marble created,
however during execution of line 9 local will move up to global.

The global variable _teacher_ will change to “Suzy” 

and since _topic_ doesn’t exist in global scope, dynamic global variable _topic_ will be created (known as "auto-global") during run time.

#### Note :
Creating auto-globals is a bad practice as it happens in run time and is not predetermined: always declare your global variables, avoid auto globals.

![](deepimages/2.jpeg)
