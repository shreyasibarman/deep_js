# Binding Precedence

The precedence of _this_ is as follows :
1. new() 
2. call()/apply()/bind()
3. context object  
4. default (global object, except strict mode)

```javascript
var w9 = {
  tea9: "Kyle",
  ask9: function ask9(que9) {
    console.log(this.tea9, que9);
  }
};

new (w9.ask9.bind(w9))("binding precedence");
//undefined binding precedence
```

