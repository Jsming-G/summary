# IP 信息处理

## 需要考虑的问题: 是否准确、稳定?是否有访问限制?等等

### 搜狐接口

- 接口地址: https://pv.sohu.com/cityjson?ie=utf-8
- 返回信息:var returnCitySN = {"cip": "74.121.150.103", "cid": "US", "cname": "UNITED STATES"};
- eg:

```
<script src="http://pv.sohu.com/cityjson?ie=utf-8"></script>
<script type="text/javascript">
    console.log(returnCitySN["cip"]+','+returnCitySN["cname"])
</script>
```

### 太平洋接口 (http://whois.pconline.com.cn/?ip=74.121.150.103)

- eg:

```
<script src="http://whois.pconline.com.cn/ip.js"></script>
点击提示实例1: IP为 <a href="javascript:alertIp('74.121.150.103');">74.121.150.103</a>
点击显示实例1: IP为 <a href="javascript:labelIp('showIpInfo','74.121.150.103');">74.121.150.103</a>
位置信息:<span id="showIpInfo" style="color:#FF0000"></span>
```
