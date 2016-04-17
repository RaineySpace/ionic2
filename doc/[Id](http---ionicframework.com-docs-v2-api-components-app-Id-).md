
# [Id](http://ionicframework.com/docs/v2/api/components/app/Id/)
Id是一个应用程序中元素的唯一标识，可以通过它来获取到元素从而进行访问。

## 使用

```
<ion-checkbox id="myCheckbox"></ion-checkbox>
```

```
constructor(app: IonicApp) {
  this.app = app
}

ngAfterViewInit() {
  var checkbox = this.app.getComponent("myCheckbox");
  if (checkbox.checked) {
    console.log('checkbox is checked');
  }
}
```

通过IonicApp服务来访问元素。

注意：不建议使用Id，因为不能保证注册组件所在的页面是否已经被销毁或者离开当前视图。
