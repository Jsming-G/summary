# Datafeed 定义

```
import ChartUtil from './ChartUtil'; // 回调方法处理

// 其它方法已删除 想要获取详细信息请查看官方文档
class DataFeeds {
  //   constructor(store) {
  // this.store = store;
  // this.ws = store.ws;
  //   }
  onDataCallback = null;
  onRealTimeCallback = null;
  onReady(callback) {
    const defaultConfiguration = {
      symbols_type: [],
      supported_resolutions: ['1', '3', '5', '15', '30', '60', '120', '240', '360', '480', '720', '1D', '3D', '1W', '1M'],
      supports_marks: true,
      supports_timescale_marks: false,
      supports_time: false,
    };
    setTimeout(() => callback(defaultConfiguration), 0);
  }

  getBars(symbolInfo, resolution, rangeStartDate, rangeEndDate, onDataCallback, onErrorCallback, firstDataRequest) {
    ChartUtil.firstDataRequest = firstDataRequest;
    ChartUtil.firstDataRequest && (ChartUtil.to = '');
    ChartUtil.onDataCallback = onDataCallback;
  }

  subscribeBars(symbolInfo, resolution, onRealTimeCallback, listenerGUID, onResetCacheNeededCallback) {
    ChartUtil.onRealTimeCallback = onRealTimeCallback;
    // this.ws.send(JSON.stringify({ sub: this.store.sub, id: 'id11' }));
  }

  unsubscribeBars() {
    // this.ws.send(JSON.stringify({ unsub: this.store.sub, id: 'id12' }));
  }

  resolveSymbol(symbolName, onSymbolResolvedCallback, onResolveErrorCallback) {
    setTimeout(function () {
      const newSymbol = Object.assign(
        {},
        {
          timezone: 'Asia/Shanghai',
          minmov: 1,
          minmov2: 0,
          pointvalue: 1,
          session: '24x7',
          has_seconds: false,
          has_daily: true,
          has_weekly_and_monthly: true,
          has_no_volume: false,
          has_empty_bars: true,
          description: '',
          has_intraday: true,
          supported_resolutions: ['1', '3', '5', '15', '30', '60', '120', '240', '360', '480', '720', '1D', '3D', '1W', '1M'],
          pricescale: 100, //价格精度
          volume_precision: 4, //数量精度
        },
        {
          symbol: symbolName,
          ticker: symbolName,
          name: symbolName,
          //   pricescale: Math.pow(10, 4) || 8, //todo
          //   volume_precision: 3 || 3,
        }
      );
      onSymbolResolvedCallback(newSymbol);
    }, 0);
  }
}

export default DataFeeds;
```
