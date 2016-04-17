
# [Icon](http://ionicframework.com/docs/v2/api/components/icon/Icon/)
Icon会自动识别平台并使用该平台的设计Icon。

```
<!-- 自动的识别平台并使用该平台的icon -->
<ion-icon name="star"></ion-icon>

<!-- 手动设置ios和android平台的图标 -->
<ion-icon ios="ios-home" md="md-home"></ion-icon>

<!-- 总是使用同一个图标，无论什么平台 -->
<ion-icon name="ios-clock"></ion-icon>
<ion-icon name="logo-twitter"></ion-icon>

<!-- 可变的name属性,myIcon是 -->
<ion-icon [name]="myIcon"></ion-icon>
```

## 属性

- name `string`
- ios `string`
- md `string`
- isActive `bool`

	设置该图标是否是活跃的图标。一般会用在tabbar中来将选中的tab图标置为活跃。
