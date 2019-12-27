# _new_ Binding

- _new_ keyword "seems" to be invoking class constructors.
- But the purpose of _new_ is to invoke a function with _this_ keyword pointing at a whole new empty object.

It does 4 things done by _new_ while invoking a function :

- A brand new object is created.
- Links that object to another object. *more
- Calls the function with this set to the new object.
- Unless the function returns Object, it assumes return of 'this'.

```javascript
function ask(ques){
  console.log(this.teacher,ques);
}
var newemptyobj = new ask("what is this?")
//undefined what is this?
```

```javascript
function f10(a) {
	this.a = a;
}

var x = new f10( 2 );
console.log( x.a ); 
// 2
```
#### Note:
Another way to create an new empty object is via explicit binding, using  **f10.call({},"sup?")**.
