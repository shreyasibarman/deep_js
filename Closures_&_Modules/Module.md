## Namespace Pattern (NOT a Module)

```javascript
var workshop = { teacher : "Kyle", ask(question){
           console.log(this.teacher,question);},
};

workshop.ask("Is this a module?")
//Kyle Is this a module?
```
             
The above pattern is called a _Namespace Pattern_.
It is NOT a module because a module pattern requires the concept of **encapsulation**. It means hiding data and behaviour.

## Revealing Module Pattern 

The _Classic Module Pattern_ is also known as the _Revealing Module Pattern_.

>Modules encapsulate data and behaviour (methods) together. The state (data) of the module is held by its methods via closure.

```javascript
function Coolmodule() {
  var something = "cool";
  var another = [1, 2, 3];

  function doSomething() {
    console.log(something);
  }

  function doAnother() {
    console.log(another.join(" ! "));
  }

  return {
    doSomething: doSomething,
    doAnother: doAnother
  };
}

var fool = Coolmodule();

fool.doSomething(); // cool
fool.doAnother(); // 1 ! 2 ! 3
```
The above module has to be invoked, and hence a module instance is created. Without the execution of the outer function, the creation of the inner scope and the closures would not occur.

**We can't have a module without closure**

Also, module is created such that it exposes _minimal necessary APIs_.

## Singleton

We can also create a module in the form of IIFEs. However, it will be a **singleton** i.e. it will only have one instance.
For multiple module instances, we need to create a _module factory_.

```javascript
var fool = (function Coolmodule() {
    var something = "cool";
    var another = [1, 2, 3];

    function doSomething() {
        console.log( something );
    }

    function doAnother() {
        console.log( another.join( " ! " ) );
    }

    return {
        doSomething: doSomething,
        doAnother: doAnother
    };
})();

fool.doSomething(); // cool
fool.doAnother(); // 1 ! 2 ! 3
```

