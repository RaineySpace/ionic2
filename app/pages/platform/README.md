# Platform

用来返回当前平台信息。它比ionic V1版本复杂，并不是单纯的返回一个平台信息，还有更多的信息，例如：设备系统，手机还是平板，移动app还是浏览器。

## 实例方法

### `is(platformName)`

返回一个布尔值来表示当前平台是否是`platformName`。

注意：同一个环境下，当platformName不同时，可能不止有一个返回`true`。例如，Ipad可能返回`true`的platformName有：`mobile` `ios` `ipad` `tablet`等。

可能有的平台名有：

- android
- cordova
- core
- ios
- ipad
- iphone
- mobile
- mobileweb
- phablet
- tablet
- windows

```
import {Platform} from 'ionic-angular';

@Page({...})
export MyPage {
   constructor(platform: Platform) {
     if (platform.is('ios')) {
       // what ever you need to do
       // if the platform is ios
     }
   }
}
```

### `platforms()`

返回一个平台数组。

同一个环境下，可能会返回多个平台信息。

### `versions(platformName)`

返回一个包含系统相关信息的对象。

### `ready()`

返回一个`Promise`来表示设备是否准备好开始运行程序了。

### `setDir(dir)`

设置文字的排列方向。

- dir `string`

	ltr代表从左到右的排列
	rtl代表从右到左的排列

### `dir()`

返回文字排列方向。

### `isRTL()`
返回一个布尔值，来表示当前文本是否是从右到左排列的。

### `setLang(language)`

设置语言。

- language `string`

	`en-US` `en-GB` `ar` `de` `zh` `es-MX`等。

### `lang()`

返回当前语言

