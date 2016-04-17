# [App](http://ionicframework.com/docs/v2/api/decorators/App/)

app是一个ionic的装饰器，它可以启动应用，是整个ionic应用的主入口。通过一系列的参数作为应用程序的全局配置变量。`@App`可以接受一个模板属性或者一个模板地址。

```
import {App} from 'ionic-angular';

@App({
  templateUrl: 'app/app.html',
  providers: [DataService]
})

export class MyApp{
  // Anything we would want to do at the root of our app
}
```

### 属性

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| config|`object`|app的配置信息|
| prodMode|`boolean`|激活Angular的生产模式，在框架内关闭断言和其他检查。默认是`false`。
| pipes|`array`
| providers |`array`
| template |`string `
| templateUrl |`string `


