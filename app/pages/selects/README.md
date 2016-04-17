## Select
`ion-select`和html中的select有点相似。

## 单选

```
<ion-item>
  <ion-label>Gender</ion-label>
  <ion-select [(ngModel)]="gender">
    <ion-option value="f" checked="true">Female</ion-option>
    <ion-option value="m">Male</ion-option>
  </ion-select>
</ion-item>
```

## 多选

```
<ion-item>
  <ion-label>Toppings</ion-label>
  <ion-select [(ngModel)]="toppings" multiple="true">
    <ion-option>Bacon</ion-option>
    <ion-option>Black Olives</ion-option>
    <ion-option>Extra Cheese</ion-option>
    <ion-option>Mushrooms</ion-option>
    <ion-option>Pepperoni</ion-option>
    <ion-option>Sausage</ion-option>
  </ion-select>
<ion-item>
```

## Alert按钮

默认为`Cancel`和`OK`

```
<ion-select okText="Okay" cancelText="Dismiss">
  ...
</ion-select>

```

## Alert选项

使用`alertOptions`可以覆盖Alert的配置。例如可以更改标题。

```
<ion-select [alertOptions]="alertOptions">
  ...
</ion-select>

this.alertOptions = {
  title: 'Pizza Toppings',
  subTitle: 'Select your toppings'
};
```

## 输入

- multiple `boolean`

	是否可以接受多个选项

- disabled `boolean`

	组件是否被禁用

## 输出事件

- change

	当选项改变时触发

- cancel

	取消时触发
