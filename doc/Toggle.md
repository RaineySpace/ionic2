
# Toggle

```
<ion-list>

  <ion-item>
    <ion-label>Pepperoni</ion-label>
    <ion-toggle [(ngModel)]="pepperoni"></ion-toggle>
  </ion-item>

  <ion-item>
    <ion-label>Sausage</ion-label>
    <ion-toggle [(ngModel)]="sausage" disabled="true"></ion-toggle>
  </ion-item>

  <ion-item>
    <ion-label>Mushrooms</ion-label>
    <ion-toggle [(ngModel)]="mushrooms"></ion-toggle>
  </ion-item>

</ion-list>

```

## 属性

- checked `boolean`

	是否打开

- disabled `boolean`

	是否禁用

## 输入

- checked
- disabled

## 输出事件

- change

	切换时触发