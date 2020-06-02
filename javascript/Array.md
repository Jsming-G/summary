# Array 方法

- 方法

| 方法     | 描述                                                           |
| -------- | :------------------------------------------------------------- |
| concat   | 连接两个或更多的数组，并返回结果。                             |
| join     | 把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。 |
| pop      | 删除并返回数组的最后一个元素                                   |
| push     | 向数组的末尾添加一个或更多元素，并返回新的长度。               |
| reverse  | 颠倒数组中元素的顺序。                                         |
| shift    | 删除并返回数组的第一个元素                                     |
| slice    | 从某个已有的数组返回选定的元素                                 |
| sort     | 对数组的元素进行排序                                           |
| splice   | 删除元素，并向数组添加新元素。                                 |
| unshift  | 向数组的开头添加一个或更多元素，并返回新的长度。               |
| valueOf  | 返回数组对象的原始值                                           |
| toString | 把数组转换为字符串，并返回结果。                               |

- 对比

| 方法 1  | 方法 2  | 描述                         |
| ------- | ------- | ---------------------------- |
| push    | unshift | 尾、头,添加,返回长度         |
| pop     | shift   | 尾、头,删除,返回删除个数     |
| splice  |         | 截取(位置,格式,插入记录)     |
| slice   |         | 截取 (起始-包括,终止-不包括) |
| contact | join    | 不操作数组本身               |
| sort    | reverse | 操作数组本身                 |

- 数组排序，{type} 1：从小到大 2：从大到小 3：随机

```javascript
const sort = (arr, type = 1) => {
  return arr.sort((a, b) => {
    switch (type) {
      case 1:
        return a - b;
      case 2:
        return b - a;
      case 3:
        return Math.random() - 0.5;
      default:
        return arr;
    }
  });
};
```
