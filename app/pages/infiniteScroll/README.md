
# [InfiniteScroll](http://ionicframework.com/docs/v2/api/components/infinite-scroll/InfiniteScroll/)

当用户滚动到页面底部时，可以通过InfiniteScroll执行一个动作。

可以用来实现上拉加载。

## 使用方法

```
<ion-content>

 <ion-list>
   <ion-item *ngFor="#i of items"></ion-item>
 </ion-list>

 <ion-infinite-scroll (infinite)="doInfinite($event)">
   <ion-infinite-scroll-content></ion-infinite-scroll-content>
 </ion-infinite-scroll>

</ion-content>
```

```
@Page({...})
export class NewsFeedPage {

  constructor() {
    this.items = [];
    for (var i = 0; i < 30; i++) {
      this.items.push( this.items.length );
    }
  }

  doInfinite(infiniteScroll) {
    console.log('Begin async operation');

    setTimeout(() => {
      for (var i = 0; i < 30; i++) {
        this.items.push( this.items.length );
      }

      console.log('Async operation has ended');
      infiniteScroll.complete();
    }, 500);
  }

}
```

## Infinite Scroll Content

```
<ion-content>

  <ion-infinite-scroll (infinite)="doInfinite($event)">
    <ion-infinite-scroll-content
      loadingSpinner="bubbles"
      loadingText="Loading more data...">
    </ion-infinite-scroll-content>
  </ion-infinite-scroll>

</ion-content>

```

## 实例方法

### `state()`

### `complete()`
调用该方法来表示加载已经完成。

### `enable(shouldEnable)`
调用该方法可以设置InfiniteScroll是否处于激活状态。当shouldEnable是`false`时，InfiniteScroll将被禁用。
- shouldEnable `boolean`

## 属性

- threshold `string`

	设置滚动触发的阙值。例如距离底部还有10%的时候触发事件。

## 输出事件

- infinite
