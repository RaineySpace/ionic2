
# [Refresher](http://ionicframework.com/docs/v2/api/components/refresher/Refresher/)

用来实现下拉刷新功能。

## 使用方法

```
<ion-content>

  <ion-refresher (refresh)="doRefresh($event)">
    <ion-refresher-content></ion-refresher-content>
  </ion-refresher>

	<!-- 其他代码 -->

</ion-content>
```

```
@Page({...})
export class NewsFeedPage {

  doRefresh(refresher) {
    console.log('Begin async operation', refresher);

    setTimeout(() => {
      console.log('Async operation has ended');
      refresher.complete();
    }, 2000);
  }

}
```

## Refresher Content

```
<ion-content>

  <ion-refresher (refresh)="doRefresh($event)">
    <ion-refresher-content
      pullingIcon="arrow-dropdown"
      pullingText="Pull to refresh"
      refreshingSpinner="circles"
      refreshingText="Refreshing...">
    </ion-refresher-content>
  </ion-refresher>

</ion-content>
```

## 实例方法

### `state`

获取当前的刷新状态。状态有：

- `inactive`

	没有下拉，被隐藏状态

- `pulling`

	用户正在下拉，但还没松手。

- `cancelling`

	用户下拉放手后，没有达到触发刷新的距离的状态。

- `ready`

	用户下拉的足够远，如果放手就开始更新。

- `refreshing`

	正在刷新，等待异步操作结束。

- `completing`

	刷新成功的状态。

### `startY`
返回用户开始下拉的Y坐标

### `currentY`
返回当前触摸或鼠标事件的Y坐标。

### `deltaY`
返回开始下拉的Y坐标距离当前触摸或鼠标事件的Y坐标的差值。

### `progress`
0代表还没有到达某个距离，不触发刷新，1代表已经到达某个距离，松手触发刷新。

### `complete()`
当你异步操作完成后，调用这个函数来关闭刷新动画，同时改变了状态。

### `cancel()`
将状态从`refreshing`改变成`cancelling`

## 输入

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|pullMin|number|用户最小的下拉距离，默认为60|
|pullMax|number|用户下拉的最大距离，超过该距离后，自动进入刷新。默认最大距离为：pullmin+60。
|closeDuration|number|多少毫秒它需要关闭组件，默认为280|
| snapbackDuration|number|默认280|
|enabled|boolean|是否启用该组件|

## 输出事件

- `refresh`

	刷新事件。不要忘记在异步事件执行完成后调用`complete()`

- `pulling`

	当用户下拉的时候调用。

- `start`

	当用户开始下拉的时候调用。

