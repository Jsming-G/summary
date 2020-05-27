# Url 参数操作

- 获取 url 参数

```javascript
function getURLParameters(url) {
  return url.match(/([^?=&]+)(=([^&]*))/g).reduce((a, v) => ((a[v.slice(0, v.indexOf('='))] = v.slice(v.indexOf('=') + 1)), a), {});
}
```
