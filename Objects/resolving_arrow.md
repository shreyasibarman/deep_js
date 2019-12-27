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
