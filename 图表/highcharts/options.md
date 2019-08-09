# option 配置

## plotOptions

```javascript
plotOptions:{
    spline:{
        lineWidth: 1, // 线宽度
        states: {
            hover: {
                lineWidth: 1 // 选中线款
            }
        },
        pointInterval: 3600000, // 间隔时间 one hour
        pointStart: Date.UTC(2018, 1, 13, 0, 0, 0) // 开始刻度
    }
}
```
