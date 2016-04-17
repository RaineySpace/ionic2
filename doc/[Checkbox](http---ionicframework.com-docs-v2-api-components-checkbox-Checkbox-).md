
# [Checkbox](http://ionicframework.com/docs/v2/api/components/checkbox/Checkbox/)

复选框拥有一个布尔值来标记自己是否被选中，使用`checked`可以来默认选中复选框，使用`disabled`来禁用该复选框。

```
<ion-item>
  <ion-label>Daenerys Targaryen</ion-label>
  <ion-checkbox dark checked="true"></ion-checkbox>
</ion-item>

<ion-item>
  <ion-label>Arya Stark</ion-label>
  <ion-checkbox disabled="true"></ion-checkbox>
</ion-item>

<ion-item>
	<ion-label>Jon Snow</ion-label>
   	<ion-checkbox [(ngModel)]="sausage"></ion-checkbox>
</ion-item>
```

## 特性

- checked `boolean`

	复选框是否被选中

- disabled `boolean`

	复选框是否禁用

## 事件

- change

	当复选框状态变化时触发