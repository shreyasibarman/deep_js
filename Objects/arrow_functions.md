# Arrow Functions & Lexical _this_

```javascript
var workshop = {
  teacher : "kyle",
  ask(question){
    setTimeout(()=>{console.log(this.teacher,question);},100);
  },
};

workshop.ask("is this lexical 'this'?");
// kyle is this lexical 'this'?
```
- Misconception : Arrow function is a hardbound function.
- Truth : Arrow function doesn't define a _this_ keyword (neither new,super,etc.)
- Hence, it will behave like any other variable, i.e. lexically, that is why its called **lexical this**
- It goes up a scope from _setTimeout_ function to _ask_ function.
- In ask the definition of _this_ depends on line 10 (workshop.ask) and hence points to the _teacher_ of workshop object.

# Resolving _this_ in Arrow Functions

```javascript
var workshop = {
  teacher : "kyle",
  ask : (question) => {
    console.log(this.teacher,question);
  },
};

workshop.ask("What happened to 'this'?");
//undefined What happened to 'this'?

workshop.ask.call(workshop,"What happened to 'this'?");
//undefined What happened to 'this'?
```
- Misconception - curly braces are scopes, hence we assume the _this_ in the above code will go check in _workshop_ object. Object is not a scope.
- Truth - It goes to the above scope which is **global** and hence returns undefined.
- Only right time to use arrow function is to use it when you can benefit from lexical this behaviour
