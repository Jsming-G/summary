# nginx 编译安装

- 下载 nginx (http://nginx.org/en/download.html)

```
# 解压
tar -xzvf nginx-1.18.0.tar.gz

# 安装依赖
yum -y install pcre-devel openssl openssl-devel

# 进入目录执行
./configure --prefix=/usr/local/nginx-1.18.0
```

- geoIP (下载:http://nginx.org/packages/mainline/ubuntu/pool/nginx/n/nginx-module-geoip/)
