# Url 参数操作

- 获取 url 参数

```javascript
function getURLParameters(url) {
  return url.match(/([^?=&]+)(=([^&]*))/g).reduce((a, v) => ((a[v.slice(0, v.indexOf('='))] = v.slice(v.indexOf('=') + 1)), a), {});
}
```

```javascript
const reg = new RegExp('(^|&)' + name + '=([^&]*)(&|$)', 'i');
const search = window.location.search.split('?')[1] || '';
const r = search.match(reg) || [];
return r[2];
```

- 追加 url 参数

```javascript
const appendQuery = (url, key, value) => {
  var options = key;
  if (typeof options == 'string') {
    options = {};
    options[key] = value;
  }
  options = $.param(options);
  if (url.includes('?')) {
    url += '&' + options;
  } else {
    url += '?' + options;
  }
  return url;
};
```
