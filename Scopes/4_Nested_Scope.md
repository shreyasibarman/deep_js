# Nested Scope



In line 7 _teacher_ is in blue scope and _question_ is in green scope because parameter is **formally creating an identifier in that scope**

They keep going one up looking for the variables, hence _teacher_ is blue, since no _question_ exists, its just a green marble with no value which later gets assigned “why” during runtime.


In line 14 _ask_ gives _Reference Error_ because red scope doesn’t have _ask_ identifier within it (its within blue scope)


#### Note :
Unlike Auto Globals, when  a ‘source’ is asked for, it's global won’t create it automatically.

![](deepimages/4.jpeg)
