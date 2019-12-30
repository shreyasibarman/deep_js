# Prototypal Class

```javascript
function workshop(teacher) {
  this.teacher = teacher;
}

//ask-property
workshop.prototype.ask = function(question) {
  console.log(this.teacher, question);
};

var ins1 = new workshop("kyle");
var ins2 = new workshop("suzy");

ins1.ask("is this prototype?");
ins2.ask("is this prototype?");

// kyle is this prototype? 
// suzy is this prototype?
```
- Objects are built by _"constructor calls"_ (via the _new_ keyword).
- When we use _new_ in front of a function call, it's constructing an object to be used for this binding of that function call.
- It is said that the "constructor calls" are making the objects ~based on~ the constructor’s prototype.
- The term "based on" above is not technicalluy true because JS doesn't make a copy of prototype when an object is created (like in other object oriented languages), It makes it linked to the prototype. So the correct way to say it would be :
- "Constructor calls" are making the objects _linked to_ the constructor’s prototype.

# The Prototype Chain





