# rem-adaper
基于less自动生成rem适配方案

#### 根据设计稿尺寸自动生产rem适配方案

> less 文件配置

* 只需要根据设计图修改psdWidth设计稿尺寸参数即可

```javascript
@charset "UTF-8";
// 设备尺寸
@adapterDeviceList:750px,720px,640px,540px,480px,424px,414px,400px,384px,375px,360px,320px;
// 设计稿尺寸
@psdWidth: 750px;
// 基准字体大小
@baseFontSize:100px;
// 设备数
@len:length(@adapterDeviceList);
// 适配方案函数: 根据设计图动态生成适配方案
.adapterMixin(@index) when ( @index > 0){
  @media (min-width: extract(@adapterDeviceList,@index)){
    html{
      font-size: @baseFontSize / @psdWidth * extract(@adapterDeviceList,@index);
    }
  }
  .adapterMixin( @index - 1);
}
// 函数调用
.adapterMixin(@len);
```

> 自动生产css适配方案

```javascript
@charset "UTF-8";
@media (min-width: 320px) {
  html {
    font-size: 42.66666667px;
  }
}
@media (min-width: 360px) {
  html {
    font-size: 48px;
  }
}
@media (min-width: 375px) {
  html {
    font-size: 50px;
  }
}
@media (min-width: 384px) {
  html {
    font-size: 51.2px;
  }
}
@media (min-width: 400px) {
  html {
    font-size: 53.33333333px;
  }
}
@media (min-width: 414px) {
  html {
    font-size: 55.2px;
  }
}
@media (min-width: 424px) {
  html {
    font-size: 56.53333333px;
  }
}
@media (min-width: 480px) {
  html {
    font-size: 64px;
  }
}
@media (min-width: 540px) {
  html {
    font-size: 72px;
  }
}
@media (min-width: 640px) {
  html {
    font-size: 85.33333333px;
  }
}
@media (min-width: 720px) {
  html {
    font-size: 96px;
  }
}
@media (min-width: 750px) {
  html {
    font-size: 100px;
  }
}
/*# sourceMappingURL=adapter.css.map */
```
