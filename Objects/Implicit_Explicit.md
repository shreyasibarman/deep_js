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


# Explicit Binding

```javascript
function f5(question5) {
  console.log(this.teacher5, question5);
}
var w3 = {
  teacher5: "kyle"
};

var w4 = {
  teacher5: "suzy"
};

f5.call(w3, "supp?");
f5.call(w4, "supp?");
//kyle supp? 
//suzy supp?
```
- In the above code sharing is done, but explicitly.
- *f5.call()* says "No matter where the function is from, invoke it in the particular specified context".
- _.call()_ and _.apply()_ is used to invoke functions explicitly.

### Hard Binding

```javascript
var w6 = {
  teacher6: "kyle",
  f6(question6) {
    console.log(this.teacher6, question6);
  }
};

setTimeout(w6.f6, 10, "lost when");
//undefined "lost when" 

setTimeout(w6.f6.bind(w6), 10, "hard bound when");
//kyle hard bound when 
```
- Hard binding is a variation of explicit binding.
- It is used for flexible dynamicism.
- It is recommended to use _closure_ instead if you want predictability. (i.e. no point of using hard binding if it is being used a lot, all over the program).








