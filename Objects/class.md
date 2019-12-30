# _class_ keyword (ES6)

- It is a _syntactic sugar_ layered on top of the Prototype system.

```javascript
class Workshop{
  constructor(teacher){
    this.teacher = teacher;
  }
  ask(question){
    console.log(this.teacher,question);
  }
}

var obj1 = new Workshop("kyle");
var obj2 = new Workshop("suzy");

obj1.ask("class instance 1?");
obj2.ask("class instance 2?");
// kyle class instance 1? 
// suzy class instance 2? 
```

# Extending classes

```javascript
class Workshop{
  constructor(teacher){
    this.teacher = teacher;
  }
  ask(question){
    console.log(this.teacher,question);
  }
}

class Another extends Workshop{
  speak(msg){
    this.ask(msg);
  }
}

var obj1 = new Another("kyle");

obj1.ask("class extended");
// kyle class extended 
```
# _super_ keyword

- It allows **Relative Polymorphism** : If child class and parent class have the same name ( i.e. shadowing ), we can refer to the parent from the child using _super_.
- before ES6 there was no way to do relative polymorphism, hence no equivalent of _super_ keyword.

```javascript
class Workshop{
  constructor(teacher){
    this.teacher = teacher;
  }
  ask(question){
    console.log(this.teacher,question);
  }
}

class Another extends Workshop{
  ask(msg){
    super.ask(msg.toUpperCase());
  }
}

var obj1 = new Another("kyle");

obj1.ask("using super");
// kyle USING SUPER 
```
