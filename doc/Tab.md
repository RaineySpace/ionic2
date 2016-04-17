
# Tab

底部的标签按钮

## 使用方法

一般`ion-tab`都有一个`[root]`值来加载该组件。

```
<ion-tabs>
 <ion-tab [root]="chatRoot" tabTitle="Chat" tabIcon="chat"><ion-tab>
</ion-tabs>



import {Chat} from '../chat/chat';
export class Tabs {
   constructor(){
     // here we'll set the property of chatRoot to
     // the imported class of Chat
     this.chatRoot = Chat
   }
}

```

## 输入

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|root|Page|设置根页面|
|rootParams|object|传递数据到该页面|
|tabTitle|string|页面标题
|tabIcon|string|页面图标|
|tabBadge|string|设置徽章
|tabBadgeStyle|string|设置徽章颜色

## 输出事件

- select

	选中时触发。

