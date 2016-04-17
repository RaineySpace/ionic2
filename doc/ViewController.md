# ViewController

访问当前视图的功能和信息

## 使用方法

```
import {Page, ViewController} from 'ionic-angular';
@Page....
export class MyPage{
 constructor(viewCtrl: ViewController){
   this.viewCtrl = viewCtrl;
 }
}
```

## 实例方法

- `componentType()`

- `subscribe()`

- `onDismiss()`

- `dismiss()`

- `enableBack(Check)`
检查navigation栈中是否可以返回

- `index()`
查询在当前视图navigation栈中的索引

- `isFirst()`
返回一个布尔值，来表示是否是栈中第一个视图

- `isLast()`

- `hasNavbar()`
返回一个布尔值，来表示是否拥有navBar

- `setBackButtonText(backButtonText)`
更改后退按钮的文本

- `showBackButton(Set)`

设置当前视图的后退按钮是否可见
