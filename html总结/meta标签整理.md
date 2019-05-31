# meta标签的各种使用说明

* 告诉IE浏览器，无论是否用DTD声明文档标准，IE8/9都会以IE7引擎来渲染页面

```html
<meta http-equiv="X-UA-Compatible" content="IE=7">
```

* 告诉IE浏览器，IE8/9都会以IE8引擎来渲染页面

```html
<meta http-equiv="X-UA-Compatible" content="IE=8">
```

* 告诉IE浏览器，IE8/9及以后的版本都会以最高版本IE来渲染页面

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

* IE=edge告诉IE使用最新的引擎渲染网页，chrome=1则可以激活Chrome Frame

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge,chrome=1">
```

* IOS中禁用将数字识别为电话号码/忽略Android平台中对邮箱地址的识别

```html
<meta name="format-detection" content="telephone=no, email=no" />
```

* 当网站添加到主屏幕快速启动方式，可隐藏地址栏，仅针对ios的safari

```html
<meta name="apple-mobile-web-app-capable" content="yes" />
```

> ios7.0版本以后，safari上已看不到效果

* 将网站添加到主屏幕快速启动方式，仅针对ios的safari顶端状态条的样式(可选default/black/black-translucent)

```html
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
```

* 启用360浏览器的极速模式(webkit)

```html
<meta name="renderer" content="webkit">
```

* 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓

```html
<meta name="HandheldFriendly" content="true">
```

* uc强制竖屏

```html
<meta name="screen-orientation" content="portrait">
```

* QQ强制竖屏

```html
<meta name="x5-orientation" content="portrait">
```

* UC强制全屏

```html
<meta name="full-screen" content="yes">
```

* QQ强制全屏

```html
<meta name="x5-fullscreen" content="true">
```

* UC应用模式

```html
<meta name="browsermode" content="application">
```

* QQ应用模式

```html
<meta name="x5-page-mode" content="app">
```

* windows phone 点击无高光

```html
<meta name="msapplication-tap-highlight" content="no">
```

* 

```html

```

* 

```html

```

* 

```html

```

* 

```html

```

* 

```html

```

* 

```html

```