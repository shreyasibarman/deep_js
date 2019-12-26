# What is Closure?

Closure can be defined as
> When a function “remembers” it’s lexical scope even when the function is executed outside that lexical scope (or a different scope).

It works even when a scope in which it was originally defined in is conceptually gone away, if the function survived that was within that scope, didn’t go away, it is able to _hold the reference to that scope and continues to have access_.

### Preservation of scope : 
Closure is the linkage back to the original scope when it was defined (no matter when it is executed, it retains the value).
Closure doesn’t capture values, it preserves access to the variables (in more detail in next chapter).
JS implements closure as linkage to the _entire_ scope, not per variable basis. 

Closure is a _scope-based function_ because **it works per scope, not per variable.**

<img src="deepimages3/1.jpeg" width="600px" height="450px">

