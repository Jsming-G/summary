# nginx拦截指定国家或城市跳转页面

## 参考 https://www.jb51.net/article/86850.htm

- 安装 Nginx

```python
$ sudo apt-get install nginx
```

- 安装 Geoip 模块

```python
$ wget http://geolite.maxmind.com/download/geoip/api/c/GeoIP-1.4.8.tar.gz
$ ./configure
$ make
$ make install
```
或
```python
$ sudo apt-get install nginx-module-geoip
```

- 下载 Geoip 数据文件，解压，复制到 /etc/nginx/geoip 备用

```python
$ wget http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz # ip数据

$ wget http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz # 城市数据

$ gzip -d -k GeoLiteCity.dat.gz

$ sudo mkdir /etc/nginx/geoip

$ sudo cp GeoLiteCity.dat  /etc/nginx/geoip
```

- 配置 Nginx，实现 Geoip 根据 IP 识别城市，并跳转不同页面的功能

1. 在 nginx.conf 中设置 Geoip City 数据库入口

```python
$ sudo vi /etc/nginx/nginx.conf
```

在 http 里面添加下面代码：

```python
$ geoip_city /etc/nginx/geoip/GeoLiteCity.dat;
```

2. 配置 default 文件

```python
$ sudo vi /etc/nginx/sites-available/default
```

在location中增加以下代码：
```python
set $flag 0;

if ( $http_user_agent ~ "(baidu.Transcoder)|(mini)|(Android)|(blackberry)|(googlebot-mobile)|(iemobile)|(Mobile)|(ipad)|(iphone)|(ipod)|(opera mobile)|(palmos)|(webos)|(ucweb)|(Windows Phone)|(Symbian)|(hpwOS)" ) {
    set $flag "${flag}1";
}

if ($geoip_city_country_code = "CN") {
    set $flag "${flag}2";
}

if ($geoip_region_name ~ "(Beijing|Shanghai)") {
    set $flag "${flag}3";
}

if ($geoip_region_name ~ "(Guangdong)") {
    set $flag "${flag}4";
}

if ($geoip_city ~ "(Guangzhou|Shenzhen)") {
    set $flag "${flag}5";
}

# The ip in China but not in Beijing Shanghai Guangdong
if ($flag = "012") {
    set $flag 1;
}

# The ip in China Guangdong but not in Guangzhou Shenzhen
if ($flag = "0124") {
    set $flag 1;
}

if ($flag = "1") {
    root /home/ubuntu/www/your/dir;
}
```