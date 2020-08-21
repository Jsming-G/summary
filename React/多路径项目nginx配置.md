# 多路径项目 nginx 配置

- 首先，需要配置 publicUrl，这个是静态文件的前缀。 从 config/paths.js 中可以看到该配置即可通过 env.PUBLIC_URL 传入，也可配置在 package.json 中，
  本文采用的是后一种的方法：

```
...
"homepage": "/aaa"
...
```

- 然后，react-router 需要配置 basename 作为路由的前缀:

```
...
<BrowserRouter basename='/aaa'>
    <App />
</BrowserRouter>
...
```

- nginx 配置

```
location /aaa {
    try_files $uri /aaa/index.html;
}

location = /aaa/index.html {
    alias /www/aaa/build/index.html;
}
# 静态资源配置
location /aaa/static/ {
    alias  /www/aaa/build/static/;
}
# 代理配置
location /api {
    proxy_pass http://XXXX.com;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
}
```

> 查考地址: https://www.dazhuanlan.com/2020/02/05/5e3a1e49d9400/
>
> https://segmentfault.com/a/1190000013218418?utm_source=tag-newest
