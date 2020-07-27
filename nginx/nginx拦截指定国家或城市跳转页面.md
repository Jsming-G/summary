# nginx 拦截指定国家或城市跳转页面

### 参考(https://www.cnblogs.com/rvs-2016/p/12552376.html)

- 下载 nginx (http://nginx.org/en/download.html)

```
# 解压
tar -xzvf nginx-1.18.0.tar.gz

# 安装依赖
yum -y install pcre-devel openssl openssl-devel

# 安装
./configure --prefix=/usr/local/nginx
```

- 下载 GeoIP

```
# 解压
tar -xzvf GeoIP-1.4.8

# 安装
./configure && make && make install

# /usr/local/share/GeoIP/下会生成GeoIP.dat文件
```

- 安装 nginx 的 GeoIP 模块

```
# 进入 nginx-1.18.0
./configure --prefix=/usr/local/nginx --with-http_geoip_module && make && make install
```

- nginx 配置

```
geoip_country /usr/local/share/GeoIP/GeoIP.dat;
fastcgi_param GEOIP_COUNTRY_CODE $geoip_country_code;
# fastcgi_param GEOIP_COUNTRY_CODE3 $geoip_country_code3;
# fastcgi_param GEOIP_COUNTRY_NAME $geoip_country_name;

server {
    listen  80;
    server_name www.test.com;

    location / {
        if ($geoip_country_code = CN) {
            # proxy_pass http://address.com

            root /drep/exchange/ip-jump; # 跳转的目录

            # 上面无法跳转可配置重定向指定页面
            # rewrite ^/(.*) http://your_server_name:81/ break;
        }
    }
}
```

# 后期完善记录

```
------- 未成功
# nginx 模块包未实现,后期可尝试,以下是地址
http://nginx.org/packages/mainline/ubuntu/pool/nginx/n/nginx-module-geoip/
-------
```

```
# geoip 数据包下载地址 -- 新版
https://www.maxmind.com/en/accounts/365749/geoip/downloads
```
