# requestAnimationFrame

### 模块化开发

```javascript
// eslint-disable
window.requestNextAnimationFrame = (() => {
  let origonalWebkitMethod;
  let wrapper;
  let geckoVersion = 0;
  const { userAgent } = navigator;
  let index = 0;

  // Workaround for Chrome 10 bug where Chrome does not pass the time to the animation function
  if (window.webkitRequestAnimationFrame) {
    wrapper = (time) => {
      let temp = time;
      if (temp === undefined) {
        temp = +new Date();
      }
      this.callback(temp);
    };
    // Make the switch
    origonalWebkitMethod = window.webkitCancelAnimationFrame;
    window.webkitCancelAnimationFrame = (callback, element) => {
      this.callback = callback;
      // Browser calls wrapper; wrapper calls callback
      origonalWebkitMethod(wrapper, element);
    };
  }

  // Workaround for Gecko 2.0, which has a bug in mozRequestAnimationFrame() that restricts animations to 30-40 fps
  if (window.mozRequestAnimationFrame) {
    // Check the Gecko version. Gecko is used by browsers other than Firefox. Gecko 2.0 corresponds to Firefox 4.0
    index = userAgent.indexOf('rv:');
    if (userAgent.indexOf('Gecko') !== -1) {
      geckoVersion = userAgent.substr(index + 3, 3);
      if (geckoVersion === '2.0') {
        // Forces the return statement to fall through to the setTimeout() function
        window.mozRequestAnimationFrame = undefined;
      }
    }
  }
  return (
    window.requestAnimationFrame ||
    window.webkitRequestAnimationFrame ||
    window.mozRequestAnimationFrame ||
    window.oRequestAnimationFrame ||
    window.msRequestAnimationFrame ||
    // eslint-disable-next-line
    function (callback) {
      let start;
      let finish;
      window.setTimeout(() => {
        start = +new Date();
        callback(start);
        finish = +new Date();
        this.timeout = 1000 / 60 - (finish - start);
      }, this.timeout);
    }
  );
})();
```

### 纯js

```javascript
window.requestNextAnimationFrame = (function () {
  var origonalWebkitMethod,
    wrapper = undefined,
    callback = undefined,
    geckoVersion = 0,
    userAgent = navigator.userAgent,
    index = 0,
    self = this;

  // Workaround for Chrome 10 bug where Chrome does not pass the time to the animation function
  if (window.webkitRequestAnimationFrame) {
    wrapper = function (time) {
      if (time === undefined) {
        time = +new Date();
      }
      self.callback(time);
    };
    // Make the switch
    origonalWebkitMethod = window.webkitCancelAnimationFrame;
    window.webkitCancelAnimationFrame = function (callback, element) {
      self.callback = callback;
      // Browser calls wrapper; wrapper calls callback
      origonalWebkitMethod(wrapper, element);
    };
  }

  // Workaround for Gecko 2.0, which has a bug in mozRequestAnimationFrame() that restricts animations to 30-40 fps
  if (window.mozRequestAnimationFrame) {
    // Check the Gecko version. Gecko is used by browsers other than Firefox. Gecko 2.0 corresponds to Firefox 4.0
    index = userAgent.indexOf('rv:');
    if (userAgent.indexOf('Gecko') != -1) {
      geckoVersion = userAgent.substr(index + 3, 3);
      if (geckoVersion === '2.0') {
        // Forces the return statement to fall through to the setTimeout() function
        window.mozRequestAnimationFrame = undefined;
      }
    }
  }
  return (
    window.requestAnimationFrame ||
    window.webkitRequestAnimationFrame ||
    window.mozRequestAnimationFrame ||
    window.oRequestAnimationFrame ||
    window.msRequestAnimationFrame ||
    function (callback, element) {
      var start, finish;
      window.setTimeout(function () {
        start = +new Date();
        callback(start);
        finish = +new Date();
        self.timeout = 1000 / 60 - (finish - start);
      }, self.timeout);
    }
  );
})();
```
