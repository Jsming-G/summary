# call()和apply()

- call

```javascript
function CountNumber(a, b, c) {
  this.a = a;
  this.b = b;
  this.c = c;
}
let myObject = new Object();
alert(myObject.a); // undefined
CountNumber.call(myObject, 12, 23, 34);
alert(myObject.a); // 12
```

- apply

```javascript
function CountNumber(a, b, c) {
  this.a = a;
  this.b = b;
  this.c = c;
}
let myObject = new Object();
alert(myObject.a); // undefined
CountNumber.apply(myObject, [12, 23, 34]);
alert(myObject.a); // 12
```

- call() 和 apply() 的区别？

call 与 apply 只是传参的形式不一样，调用参数的时候，call 是把多个参数用逗号隔开，apply 是把多个参数放在数组中
