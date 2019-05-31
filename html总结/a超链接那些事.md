# 超链接电话邮箱使用

* 打电话

```html
<a href="tel:021-10086">打电话给:021-10086</a>
```

* 发短信，winphone系统无效

```html
<a href="sms:10086">发短信给: 10086</a>
```

* 普通邮件

```html
<a href="mailto:307344322@qq.com">点击我发邮件</a>
```

* 收件地址后添加?cc=开头，可添加抄送地址（Android存在兼容问题）

```html
<a href="mailto:307344322@qq.com?cc=jamin3587@163.com">点击我发邮件</a>
```

* 跟着抄送地址后，写上&bcc=,可添加密件抄送地址（Android存在兼容问题）

```html
<a href="mailto:307344322@qq.com?cc=jamin3587@163.com&bcc=gym3587@163.com">点击我发邮件</a>
```

* 包含多个收件人、抄送、密件抄送人，用分号(;)隔开多个邮件人的地址

```html
<a href="mailto:307344322@qq.com;jamin3587@163.com">点击我发邮件</a>
```

* 包含主题，用?subject=

```html
<a href="mailto:307344322@qq.com?subject=邮件主题">点击我发邮件</a>
```

* 包含内容，用?body=;如内容包含文本，使用%0A给文本换行

```html
<a href="mailto:307344322@qq.com?body=邮件主题内容%0A腾讯诚信%0A期待您的到来">点击我发邮件</a>
```

* 内容包含链接，含http(s)://等的文本自动转化为链接

```html
<a href="mailto:307344322@qq.com?body=https://github.com/Jamin2Guan/summary">点击我发邮件</a>
```