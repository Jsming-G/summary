# 图片响应式实现及图片的那些事
### 参考地址:https://segmentfault.com/a/1190000022345867

- [srcset 属性]

```html
<img src="small.jpg" srcset="medium.jpg 500w, large.jpg 800w" alt="" />
```

- [picture 标签]

```html
<picture>
  <source srcset="large.jpg" media="(min-width: 800px)" />
  <source srcset="medium.jpg" media="(min-width: 500px)" />
  <img src="small.jpg" />
</picture>
```
