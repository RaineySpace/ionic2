# NavController

## 注入NavController

```
class MyComponent {
  constructor(nav: NavController) {
    this.nav = nav;
  }
}
```

## 页面展示

页面创建可以使用`@Page`装饰器。

当页面被添加到navigation栈的时候，页面就被展示了，使用`push()`方法。

页面销毁时将从navigation栈中移除（使用`pop()`或者`setRoot()`）。

## 生命周期

```
@Page({
  template: 'Hello World'
})
class HelloWorld {
  onPageLoaded() {
    console.log("I'm alive!");
  }
  onPageWillLeave() {
    console.log("Looks like I'm about to leave :(");
  }
}

```

- `onPageLoaded`

	当页面加载时运行，每被创建并且添加到DOM树时执行一次。如果页面切换但是被缓存下来，再次进入此页面时，将不会触发该事件。

- `onPageWillEnter`

	当页面即将进入并成为活动页时触发

- `onPageDidEnter`

	当页面完全进入成为活动页面时执行，不管是否被缓存，都将执行。

- `onPageWillLeave`

	页面即将成为非活动页时触发

- `onPageDidLeave`

	当页面切换，该页面已经成为非活动页时触发

- `onPageWillUnload`

	当页面即将被销毁时执行

- `onPageDidUnload`

	当页面已经被销毁时执行

## 实例方法

### `setRoot(page,params,opts)`

设置当前navigation栈的根节点

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|page|Type|页面的类型|
|params|object|传递到下一个视图的参数|
|opts|object|过渡选项|
返回：`Promise`

### `setPages(pages,opts)`

用来设置navigation栈。你可以用它改变navigation的历史记录和切换动画。

```
import {Page, NavController} from 'ionic-angular';
import {Info} from '../info/info';
import {List} from '../list/list';
import {Detail} from '../detail/detail';

 export class Home {
   constructor(nav: NavController) {
     this.nav = nav;
   }
   setPages() {
     this.nav.setPages([{
       page: Info
     }, {
       page: List,
       params: {tags: 'css'}
     }, {
       page: Detail,
       params: {id: 325}
     }], {
       animate: true
     });
   }
 }
```
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|pages|array<Type>|页面类型和参数组成的数组|
|opts|object|过渡选项|

返回：`Promise`

### `push(page,params,opts)`

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|page|Type|页面的类型|
|params|object|传递到下一个视图的参数|
|opts|object|过渡选项|

返回：`Promise`

### `present(enteringView,opts)`

添加组件到navigation栈中，例如：`ActionSheet` `Alert` `Modal`等

```
class MyClass{
   constructor(nav: NavController) {
     this.nav = nav;
   }

   presentModal() {
     let modal = Modal.create(ProfilePage);
     this.nav.present(modal);
   }
}
```
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|enteringView| ViewController | 组件的控制器 |
|opts|object|过渡选项|

返回：`Promise`

### `insert(insertIndex,page,params,opts)`

插入一个视图到navigation栈。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| insertIndex | number | 插入的索引 |
|page|Type|页面的类型|
|params|object|传递到下一个视图的参数|
|opts|object|过渡选项|
返回：`Promise`

### `insertPages(insertIndex,insertPages,opts)`

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| insertIndex | number | 插入的索引 |
| insertPages |array<Type>|页面类型和参数组成的数组|
|opts|object|过渡选项|
返回：`Promise`

### `pop(opts)`

如果你想后退，那么可以调用该方法。

```
class SecondView{
   constructor(nav:NavController){
     this.nav = nav;
   }
   goBack(){
     this.nav.pop();
   }
}
```

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|opts|object|过渡选项|

### `popToRoot(opts)`

直接跳转到根导航，不管在navigite栈中有多少视图。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|opts|object|过渡选项|

### `popTo(view,opts)`

将当前视图到该视图的历史记录弹出，并跳转到指定视图。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|view|ViewController|
|opts|object|过渡选项|

### `remove(startIndex,removeCount,opts)`

删除栈里指定索引段的元素。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|startIndex|number|从栈中删除页面的起始索引，默认为最后一页的索引|
|removeCount|number|从栈中删除多少个页面，默认为1|
|opts|object|过渡选项|

返回一个`Promise`

### `canSwipeBack()`

返回一个布尔值，来表示当前是否支持滑动返回

### `canGoBack()`
返回一个布尔值，来表示是否还有可返回的页面

### `getByIndex(index)`

返回指定索引的组件

### `getActive()`

返回当前活动页面的视图控制器

### `isActive(view)`

返回一个布尔值，来表示该视图是否是当前活动页面。

### `getPrevious(view)`

返回指定页面的视图控制器

### `first()`

返回当前栈中第一个的视图控制器

### `last()`

返回当前栈中最后一个的视图控制器

### `indexOf(view)`

返回某个视图在栈中的索引

### `length()`

返回栈的长度。

### `rootNav()`

返回`NavController`

