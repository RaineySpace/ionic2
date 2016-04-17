# Searchbar

管理一个搜索栏，可以搜索或筛选项目的显示。

## 使用方法

```
<ion-searchbar
  [(ngModel)]="myInput"
  [hideCancelButton]="shouldHideCancel"
  (input)="onInput($event)"
  (cancel)="onCancel($event)">
</ion-searchbar>

```

## 输入属性


| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|cancelButtonText|string|设置取消按钮的文本值|
| hideCancelButton|boolean|是否隐藏取消按钮|
|debounce|number|每次键入字符等待触发事件的时间有多长，默认为250毫秒|
| placeholder|string|占位提示符|
|ngModel|any|搜索栏值的双向绑定|

## 输出事件

- `input`

	当Searchbar中值变化的时候触发

- `blur`

	当Searchbar失去焦点的时候触发

- `focus`

	当Searchbar得到焦点的时候触发

- `cancel`

	当取消按钮被点击的时候触发

- `clear`

	当清空按钮被点击的时候触发

