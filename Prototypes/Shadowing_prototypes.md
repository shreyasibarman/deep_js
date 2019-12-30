# Shadowing Prototypes

```javascript
function workshop(teacher) {
  this.teacher = teacher;
}

workshop.prototype.ask = function(question) {
  console.log(this.teacher, question);
};

var ins1 = new workshop("kyle");

ins1.ask = function(question) {
  this.ask(question.toUpperCase());
};

ins1.ask("oops, is this infinite recursion");
```
- In the above code, when we create the same property ```ask``` in both **ins1** and **workshop.prototype**, then _this.ask_ inside _ins1.ask_ does NOT point to _workshop.prototype.ask_ like the _super_ keyword.
- There is NO **Relative Polymorphism** here.
- Its _this_ points to itself due to the call-site in the last line ```ins1.ask("oops, is this infinite recursion");```

#### So how to go one level up to access _workshop.prototype.ask_ :

```javascript
function workshop(teacher) {
  this.teacher = teacher;
}

workshop.prototype.ask = function(question) {
  console.log(this.teacher, question);
};

var ins1 = new workshop("kyle");

ins1.ask = function(question) {
  this.__proto__.ask.call(this, question.toUpperCase());
};

ins1.ask("is this fake polymorphism");
// kyle IS THIS FAKE POLYMORPHISM
```
- In the above code, ```this.__proto__.ask``` refers to **workshop.prototype.ask** and ```.call(this,---)``` invokes it by pointing this in the context of ins1.
- This call is hard-binding _this_ and is hence EXPLICIT POLYMORPHISM. There is NO Relative Polymorphism here (exists only in class system).


