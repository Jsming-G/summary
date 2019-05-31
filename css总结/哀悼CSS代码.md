# 网站代码整体变为灰色

code example:

```css
html {
    filter: progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
    filter: grayscale(100%);
    -webkit-filter: grayscale(100%);
    -moz-filter: grayscale(100%);
    -ms-filter: grayscale(100%);
    -o-filter: grayscale(100%);
    filter: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'><filter id='grayscale'><fecolormatrix type='matrix' values='0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0 0 0 1 0'></fecolormatrix></filter></svg>#grayscale");
    filter: gray;
    -webkit-filter: grayscale(1);
}
```

> 将上面代码放入全局的css样式文件中,或者放入页面的head中

-------

> FLASH处理, 在object中插入

```css
<param value="false" name="menu"/>
<param value="opaque" name="wmode"/>
```