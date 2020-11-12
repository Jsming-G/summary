# array 类型判断

- 支付宝判断方法-最全

```javascript
if (
  value instanceof Array ||
  (!(value instanceof Object) && Object.prototype.toString.call(value) == '[object Array]') ||
  (typeof value.length == 'number' && typeof value.splice != 'undefined' && typeof value.propertyIsEnumerable != 'undefined' && !value.propertyIsEnumerable('splice'))
) {
  return 'array';
}
```

- typeof 1|true|'a' 判断原始数据类型
- instanceof 复合数据类型
- Object.prototype.toString.call([]) => "[object Array]" ---最佳判断方法
