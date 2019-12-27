# Objects Overview

One of the 3 core pillars of Javascript is Objects. It is made up of :
- _this_
- _class{}_
- "Inheritance" vs "Behaviour Delegation" (OO vs. OLOO)

"Objects Oriented System" is different from "Object Oriented" because Objects oriented is not strictly a class system. There are classes layered on top of it as people prefer it, but its not inherently a class system. JS' objects system is used to implement class pattern.

```javascript
var teacher = "Kyle";

function ask(question) {
  console.log(teacher, question);
}

function otherclass() {
  var teacher = "Suzy";
  ask("Why?");
}

otherclass();
console.log("----");
// Kyle Why?
// If JS followed dynamic scoping, the result would've been - Suzy  Why?
```

# _this_ keyword

> A function's **this** references the _execution context_ of that call, determined entirely by **how the function was called** (NOT the definition of the function, but how it is called).

A _this-aware_ function can have different context each time it's called, which makes it more **flexible & usable**.

```javascript

function ask2(question2) {
  console.log(this.teacher2, question2);
}

function otherclass2() {
  var mycontext = {
    teacher2: "Suzy"
  };
  ask2.call(mycontext, "Why?");
}
otherclass2();
```

_this-aware_ functions uses ask2.call to refer to the object to be used as _this_ keyword and to invoked the function in that context.
Checks HOW the function is called, NOT WHERE.
_this_ allows dynamic flexibility, reusablibility - by allowing invokation of functions in different contexts.

### 4 ways to invoke function :
- Implicit Binding
- Explicit Binding
- _new_ Binding
- Default Binding



