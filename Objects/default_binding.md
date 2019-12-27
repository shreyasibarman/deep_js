# Default Binding

```javascript
var tea8 = "kyle";

function f8(ques8) {
  console.log(this.tea8, ques8);
}

function f8again(ques8) {
  "use strict";
  console.log(this.tea8, ques8);
}

f8("non strict mode");
//kyle non strict mode

f8again("strict mode");
//TypeError
```

- Here when we invoke the function using *f8()*, there's no context object, .call(), etc.
- It's a normal function call.
- There's no other rule and hence, in **non-strict mode** it will default to **global**.
- In **strict mode**, we get a **TypeError**, because here it leaves the property as _undefined_ and trying to invoke an undefined property gives a TypeError.
 (the behaviour is so, because it is certainly an error on the programmers part to define a this-aware function and invoke it without any this).
