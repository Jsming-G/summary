# Ajax 文件下载

```javascript
// 参考:
// https://blog.csdn.net/xmh594603296/article/details/84259794
// https://www.jianshu.com/p/154ba49d9b7a

axios({
  method: 'post',
  url: '/cmdb/UploadDownload/UploadExcel?token=' + self.$store.state.app.token,
  data: json,
  responseType: 'blob',
})
  .then((response) => {
    debugger;
    if (!response) {
      return;
    }
    //在微软Edge浏览器下无法使用createObjectURL生成的blob链接,
    //使用 window.navigator.msSaveOrOpenBlob(blob, filename)，代替window.URL.createObjectURL。
    if ('msSaveOrOpenBlob' in navigator) {
      window.navigator.msSaveOrOpenBlob(new Blob([data], { type: 'application/vnd.ms-excel;charset=utf-8' }), this.sheetName + '.xlsx');
    } else {
      let url = window.URL.createObjectURL(new Blob([response]));
      let link = document.createElement('a');
      link.style.display = 'none';
      link.href = url;
      link.setAttribute('download', 'cmdbCiTemplate.xlsx');
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link); //下载完成移除元素
      window.URL.revokeObjectURL(url); //释放blob对象
    }
  })
  .catch((error) => {});
```
