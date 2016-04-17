# Segment
Segment是一组按钮，允许用户和一组按钮进行交互，类似于标签页的功能。

## 使用方法

```
<ion-segment [(ngModel)]="relationship" (change)="onSegmentChanged($event)" danger>
  <ion-segment-button value="friends">
    Friends
  </ion-segment-button>
  <ion-segment-button value="enemies">
    Enemies
  </ion-segment-button>
</ion-segment>
```

## 输出事件

- `change`

	当按钮改变时触发事件。

