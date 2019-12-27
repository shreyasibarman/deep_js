# Implicit Binding

```javascript
var workshop4 = {
  teacher3: "abcd",
  f3(question3) {
    console.log(this.teacher3, question3);
  }
};

var workshop3 = {
  teacher3: "abc",
  f3(question3) {
    console.log(this.teacher3, question3);
  }
};

workshop4.f3("sup?");
//abcd sup?
```
- In the above code *workshop4.f3* says "invoke f3 function with this keyword pointing at workshop4".
- This is the Implicit Binding Rule : It depends on the object you call it from

### Implicit Dynamic Binding

```javascript
function f4(question4) {
  console.log(this.teacher4, question4);
}

var w1 = {
  teacher4: "kyle",
  f4: f4
};

var w2 = {
  teacher4: "suzy",
  f4: f4
};

w1.f4("supp?");
w2.f4("supp?");
//kyle supp? 
//suzy supp?
```

- Dynamic binding here means sharing of methods.
- In the above code, f4 function is being shared across 2 different objects.
- line 7 and line 12 have references to the f4 function which is used to invoke the function in different contexts. This is Implicit Binding Rule.
- It allows flexibility of _this_ which is sometimes needed in otherwise fixed and predictable lang such as JS. 




