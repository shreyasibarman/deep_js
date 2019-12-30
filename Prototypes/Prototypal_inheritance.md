# Prototypal Inheritance

```javascript
function workshop(teacher) {
  this.teacher = teacher;
}

workshop.prototype.ask = function(question) {
  console.log(this.teacher, question);
};

function anotherworkshop(teacher){
  workshop.call(this,teacher);
}

anotherworkshop.prototype = Object.create(workshop.prototype);

anotherworkshop.prototype.speakup = function(msg){
  this.ask(msg.toUpperCase());
}

var ins1 = new anotherworkshop("kyle");

ins1.speakup("is this inheritance");
// kyle IS THIS INHERITANCE
```

- In the above code we create 2 prototypes and **link** the second prototype (anotherworkshop) to the first prototype (workshop)
using ```Object.create(workshop.prototype)```
- **ins1** is linked to **anotherworkshop** linked to **workshop** via a hidden prototype chain.
- When we invoke ```ins1.speakup```---> it goes to **anotherworkshop** and checks for _speakup_, which exists and invokes ```this.ask``` ---> it checks the call-site, there is no _ask_ in **ins1** ---> check one level up, no _ask_ in **anotherworkshop** ---> checks one level up, ask exists in **workshop** so invokes _workshop.ask_.

### Classical vs. Prototypal Inheritance

