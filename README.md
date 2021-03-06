# hikvision video SDK / Cordova Plugin

![AppVeyor branch](https://img.shields.io/appveyor/ci/Eugene2799/cordova-hikvision-sdk-eugene/master)
![npm](https://img.shields.io/npm/v/cordova-hikvision-sdk-eugene)
[![platforms](https://img.shields.io/badge/platforms-Android-lightgrey)](https://github.com/Eugene2799/cordova-hikvision-sdk-eugene)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/Eugene2799/cordova-hikvision-sdk-eugene)

个人因为工作需要，封装了hikvision 的视频SDK到cordova项目中。这里目前只封装了Android的SDK。

## hikvision SDK下载及接口文档

[视频SDK-Android版本HikVideoPlayerDemo_Android_V1.3.0_build202001091556_20200110165814](https://open.hikvision.com/download/5c67f1e2f05948198c909700?type=10)

>注意：插件使用需修改src/android/libs/PreviewActivity.java和src/android/widget/AutoHideView.java中第3行，导入自己项目包的R类。
>```java
>import your.app.package.name.R;
>```

## Install

- 通过 Cordova Plugins 安装，要求 Cordova CLI 5.0+：

  ```shell
  cordova plugin add cordova-hikvision-sdk-eugene
  ```
  
- 修改plugins/cordova-hikvision-sdk-eugene/src/android/PreviewActivity.java中第3行
  ```java
  import your.app.package.name.R;
  ```

- 修改plugins/cordova-hikvision-sdk-eugene/src/android/widget/AutoHideView.java中第3行
  ```java
  import your.app.package.name.R;
  ```

## 修改完后可能需要执行的操作
- 修改完可能需要移除并重新添加cordova的android平台
  ```shell
  cordova platform remove android
  cordova platform add android
  ```

- 验证是否成功
  ```shell
  cordova build android
  ```
  提示编译成功。
  
## Usage
### init plugin 插件初始化
   ```html
   window.plugins.hikVisionSDK.init();
   ```
### start activity && set params
### 调用方法showHikVideoPage切换页面并显示监控视频
### 参数1 url为监控视频url，title为监控视频名称（title暂无UI展示区域）

```html
let param = { 'url': yourMonitorUrl, 'title': setTitle }
window.plugins.hikVisionSDK.showHikVideoPage(param,function (msg) {
  console.log(msg)
},function (err) {
  console.log(err)
});
```

## FAQ
> 如果遇到了疑问，请优先参考 代码 和 海康威视API 文档。若还无法解决，可到 [Issues](https://github.com/Eugene2799/cordova-hikvision-sdk-eugene/issues) 提问。

## 最终效果图

![效果图](http://qiniublog.whitedolphin.top/20200213213259.png)
