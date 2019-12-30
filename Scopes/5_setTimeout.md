# _setTimeout_ for _var_ and _let_


```javascript

for (var i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(`i: ${i}`);
  }, i * 0);
}
// i: 4
// i: 4
// i: 4
```

The reason the result gives 4,4,4 instead of 1,2,3 is because _i_ is only one variable, and as we studied earlier, _closure preserves access to variables (not value)_, so it preserves the value of the last instance of i.e. 4.

To recieve 3 different values, we needed 3 different variables, which can be achieved by using a **block scoped declaration** _(Solution using Scope)_

```javascript
for (var i = 1; i <= 3; i++) {
  let j = i;
  setTimeout(function() {
    console.log(`j: ${j}`);
  }, j * 0);
}
// j: 1
// j: 2
// j: 3
```

It preserves separate values of _j_ in each iteration. _j_ runs every time as the loop iterates
_New j is created in every iteration_

Or we can implement the above code as : 

```javascript
for (let i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(`i: ${i}`);
  }, i * 0);
}
// i: 1
// i: 2
// i: 3
```

In the above code the _let_ statement is actually executing inside the loop even though its written with the for statement. Happens with for, for in, for of, etc.
