# [ItemSliding](http://ionicframework.com/docs/v2/api/components/item/ItemSliding/)
创建一个可滑动的Item。

```
<ion-list>
  <ion-item-sliding *ngFor="#item of items">
    <button ion-item (click)="itemTapped(item)">

    </button>
    <ion-item-options>
      <button (click)="favorite(item)">Favorite</button>
      <button (click)="share(item)">Share</button>
    </ion-item-options>
  </ion-item-sliding>
</ion-list>
```
