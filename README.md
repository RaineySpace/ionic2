# ionic2.0@beta版本文档整理

*本文档不是英文文档的完全翻译，是个人的阅读笔记。如果阅读后有不明白或者不懂，[请移步英文版阅读](http://ionicframework.com/docs/v2/api/)。
如果本文有错误，请在本页末尾留言或者提交[Issues](https://github.com/Raineye/ionic2/issues)。*

*您可以点击小标题跳转到相应的ionic2英文文档。*

## 前言

声明：本仓库中的例子程序使用了ionic官方的例子[ionic-preview-app](https://github.com/driftyco/ionic-preview-app)。

运行：

- `git clone git@github.com:Raineye/ionic2.git`
- `cd ionic-preview-app`
- `npm install`
- `ionic serve`



## [ActionSheet](http://ionicframework.com/docs/v2/api/components/action-sheet/ActionSheet/)
ActionSheet是一个对话框，让用户选择一个选项。而且用户必须要选择其中一个选项才能恢复与应用程序的交互（点击背景会执行`cancel`的事件）。当然也可以利用背景或者后退键来取消对话框从而恢复和程序的交互。

ActionSheet会从一个`button`数组创建它的按钮选项。每一个按钮都拥有一些属性，例如`text` `handler` `role` 等等。如果`handler`返回`false`时，ActionSheet将不会消失。ActionSheet还可以选择有一个标题和副标题。

如果有一个button的`role`被设置为`cancel`那么这个按钮不管位于按钮数组的哪个位置它都会位于底部。ionic官方建议`destructive`类型的按钮最好位于数组的第一个位置。另外，如果ActionSheet是由于点击背景而被取消的，那么它将会执行和`cancle`类型的按钮点击一样的事件。

注意：如果有两个`cancle`类型的按钮，那么最后一个`cancel`类型的按钮会覆盖掉前面所有的`cancel`类型的按钮。

在创建ActionSheet的第一个参数中，你可以将所有的选项传递进去：`ActionSheet.create(opts)。

```TypeScript
  openMenu(){
    this.actionSheet = ActionSheet.create({
      title: 'Albums',
      buttons: [
         {
           text: 'Destructive',
           role: 'destructive',
           handler: () => {
             console.log('Destructive clicked');
           }
         },
         {
           text: 'Archive',
           handler: () => {
             console.log('Archive clicked');
           }
         },
         {
           text: 'Cancel',
           role: 'cancel',
           handler: () => {
             console.log('Cancel clicked');
           }
         }
       ]
    })
    this.nav.present(this.actionSheet);

  }
```
### 静态方法

#### create(opts)
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| title	           | `string`      |ActionSheet的标题    |
| subTitle| `string`|ActionSheet的副标题|
| cssClass|`string`|自定义样式的css类|
| enableBackdropDismiss|`boolean`|用户点击背景是否关闭ActionSheet|
| buttons|`array<any>`|显示的按钮的数组|


**按钮的属性**

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| text|`string`|按钮上显示的文字|
| icon|`icon`|按钮上显示的图标|
| handler|`any`|点击后执行的函数|
| cssClass|`stirng`|
|role|`string`|如何显示按钮，`destructive`或者`cancel`。如果没有设置此选项，那么将显示默认的按钮。|
### 实例方法

#### `setTitle(title)`
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| title |`string`|设置ActionSheet的标题|

#### `setSubTitle(subTitle)`
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| subTitle |`string`|设置ActionSheet的子标题|

#### `addButton(button)`
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| button |`object `| ActionSheet的按钮。 |


## [Alert](http://ionicframework.com/docs/v2/api/components/alert/Alert/)

Alert是一个对话框，可以向用户提供信息或者收集用户输入的信息。同样用户必须点击某个按钮才能销毁这个对话框。

和ActionSheet十分相似的是，点击`role`被设置成`cancle`的按钮和点击背景所触发的事件是一样的。

```
constructor(nav: NavController) {
  this.nav = nav;
}

presentAlert() {
  let alert = Alert.create({
    title: 'Low battery',
    subTitle: '10% of battery remaining',
    buttons: ['Dismiss']
  });
  this.nav.present(alert);
}

presentConfirm() {
  let alert = Alert.create({
    title: 'Confirm purchase',
    message: 'Do you want to buy this book?',
    buttons: [
      {
        text: 'Cancel',
        role: 'cancel',
        handler: () => {
          console.log('Cancel clicked');
        }
      },
      {
        text: 'Buy',
        handler: () => {
          console.log('Buy clicked');
        }
      }
    ]
  });
  this.nav.present(alert);
}

presentPrompt() {
  let alert = Alert.create({
    title: 'Login',
    inputs: [
      {
        name: 'username',
        placeholder: 'Username'
      },
      {
        name: 'password',
        placeholder: 'Password',
        type: 'password'
      }
    ],
    buttons: [
      {
        text: 'Cancel',
        role: 'cancel',
        handler: data => {
          console.log('Cancel clicked');
        }
      },
      {
        text: 'Login',
        handler: data => {
          if (User.isValid(data.username, data.password)) {
            // logged in!
          } else {
            // invalid login
            return false;
          }
        }
      }
    ]
  });
  this.nav.present(alert);
}
```

### 静态方法

#### `creat(opts)`

Alert选项

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| title|`string`|
| subTitle |`string`|
| message |`string`|Alert显示的信息|
| cssClass|`string`|
| inputs|`array`|Alert显示的输入框数组|
| buttons|`array`|
| enableBackdropDismiss|`boolean`|点击背景是否销毁Alert|


Input选项

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| type|`string`|input的类型，例如：text、tel、number等等|
| name|`string`|
| placeHolder|`string`|input的占位符，未输入时的提示信息。|
| value|`string`|checkbox的值|
| label|`string`|checkbox显示的文字|
| checked|`boolean`|是否选中|
| id|`string`|input的标识|

Button的选项

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| text|`string`|
| handler |`any `|
| cssClass |`string`|
| role |`string`|`null`或者`cancel`

### 实例方法

#### `setTitle(title)`

- title `stirng`

#### `setSubTitle(subTitle)`

#### `setMessage(message)`

#### `addButton(button)`

#### `setCssClass(cssClass)`

- cssClass `string`

	添加css class 到alert的外层。

## [App](http://ionicframework.com/docs/v2/api/decorators/App/)

app是一个ionic的装饰器，它可以启动应用，是整个ionic应用的主入口。通过一系列的参数作为应用程序的全局配置变量。`@App`可以接受一个模板属性或者一个模板地址。

```
import {App} from 'ionic-angular';

@App({
  templateUrl: 'app/app.html',
  providers: [DataService]
})

export class MyApp{
  // Anything we would want to do at the root of our app
}
```

### 属性

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| config|`object`|app的配置信息|
| prodMode|`boolean`|激活Angular的生产模式，在框架内关闭断言和其他检查。默认是`false`。
| pipes|`array`
| providers |`array`
| template |`string `
| templateUrl |`string `


## [Badges](http://ionicframework.com/docs/v2/components/#badges)

Badges是一种小部件，通常用于数值显示。

```
<ion-item>
  <ion-icon name="logo-twitter" item-left></ion-icon>
  Followers
  <ion-badge item-right>260k</ion-badge>
</ion-item>
```

Badges也可以给与颜色属性`<ion-badge secondary></ion-badge>
`

## [Buttons](http://ionicframework.com/docs/v2/api/components/button/Button/)
Button是ionic中的简单句子，可以显示文本、图标或者都显示。

### 属性

- outline

	带有边框的透明按钮

- clear

	不带边框的透明按钮

- round

	大圆角的按钮

- block

	一个填充其父容器的小圆角按钮

- full

	填充其父容器的直角按钮

- small

	一个小尺寸按钮

- large

	一个大尺寸按钮

- disabled

	一个不能点击的按钮

- fab

	一个浮动的按钮

- fab-left/fab-right/fab-center/fab-top/fab-bottom

	控制浮动按钮的位置

- color

	动态设置按钮的颜色属性。

- start\end

	在`<ion-navbar>`中的位置控制

### Icon Buttons

```
<!-- Float the icon left -->
<button>
  <ion-icon name="home"></ion-icon>
  Left Icon
</button>

<!-- Float the icon right -->
<button>
  Right Icon
  <ion-icon name="home"></ion-icon>
</button>

<!-- Only icon (no text) -->
<button>
  <ion-icon name="home"></ion-icon>
</button>
```

## [Cards](http://ionicframework.com/docs/v2/components/#cards)
Cards是一个css组件

### Card的组成

就像一个普通的页面一样，cards拥有一个头部和内容。

```
<ion-card>
  <ion-card-header>
    Header
  </ion-card-header>

  <img src="img/nin-live.png"/>

  <ion-card-content>
    The British use the term "header", but the American term "head-shot" the English simply refuse to adopt.
  </ion-card-content>
</ion-card>
```
## [Checkbox](http://ionicframework.com/docs/v2/api/components/checkbox/Checkbox/)

复选框拥有一个布尔值来标记自己是否被选中，使用`checked`可以来默认选中复选框，使用`disabled`来禁用该复选框。

```
<ion-item>
  <ion-label>Daenerys Targaryen</ion-label>
  <ion-checkbox dark checked="true"></ion-checkbox>
</ion-item>

<ion-item>
  <ion-label>Arya Stark</ion-label>
  <ion-checkbox disabled="true"></ion-checkbox>
</ion-item>

<ion-item>
	<ion-label>Jon Snow</ion-label>
   	<ion-checkbox [(ngModel)]="sausage"></ion-checkbox>
</ion-item>
```

### 特性

- checked `boolean`

	复选框是否被选中

- disabled `boolean`

	复选框是否禁用

### 事件

- change

	当复选框状态变化时触发

## [Config](http://ionicframework.com/docs/v2/api/config/Config/)
用来配置整个应用程序。

### 属性

| 名称          | IOS默认           |MD默认                 |
| -------------    |------------- |-------------      |
|activator|	highlight	|ripple
|actionSheetEnter|action-sheet-slide-in|action-sheet-md-slide-in
|actionSheetLeave|action-sheet-slide-out|action-sheet-md-slide-out
alertEnter|alert-pop-in	|alert-md-pop-in
alertLeave|alert-pop-out|alert-md-pop-out
backButtonText|	Back
backButtonIcon|	ion-ios-arrow-back|	ion-md-arrow-back
iconMode|	ios	|md
menuType	|reveal	|overlay
modalEnter|	modal-slide-in|	modal-md-slide-in
modalLeave|	modal-slide-out|	modal-md-slide-out
pageTransition|	ios-transition|	md-transition
pageTransitionDelay|	16|	120
tabbarPlacement	|bottom|	top
tabbarHighlight	|	|top
tabbarLayout|		
tabSubPages|		|true

### 实例方法

#### `get(key, fallbackValue)`

- key `string`

	config的键

- fallbackValue `any`

#### `getBoolean(key)`

#### `set(platform,key,value)`

- platform `string`

	"ios"或者"android"

## [Content](http://ionicframework.com/docs/v2/api/components/content/Content/)
Content组件提供了易于使用的方法来控制滚动，同时可以和其他组件配合实现下拉刷新和上拉加载的功能。

### 实例方法

#### `onScrollElementTransitionEnd()`

#### `scrollTo(x,y,duration,tolerance)`
滚动到具体的坐标

- x `number`

	x轴距离

- y `number`

	y轴距离

- duration `number`

	滚动动画的持续时间

- tolerance `TODO`


此函数执行完毕后，返回一个`Promise`

#### `scrollToTop()`

滚动到顶部，执行完毕后返回一个`Promise`

#### `getContentDimensions()`
获取content的尺寸

## [Events](http://ionicframework.com/docs/v2/api/util/Events/)
Events是一个发布订阅式的事件系统。

```
// first page (publish an event when a user is created)
function createUser(user) {
  console.log('User created!')
  events.publish('user:created', user);
}

// second page (listen for the user created event)
events.subscribe('user:created', (user) => {
  console.log('Welcome', user);
});

```

### 实例方法

#### `subscribe(topic,handler)`

订阅某个事件，当有该事件被发布时，执行handler。

- topic `string`

	订阅的主题

- handler `function`

#### `unsubscribe(topic, handler)`
取消订阅某个主题。handler不再接受该主题发布的事件。

如果handler成功移除，改函数返回`true`

#### `publish(topic,eventData)

将事件发布到给定的主题

## [Grid](http://ionicframework.com/docs/v2/components/#grid)

ionic基于flexbox制作了一套网格框架。

```
<ion-col width-10>This column will take 10% of space</ion-col>
```

列的百分比属性：

- width-10	10%
- width-20	20%
- width-25	25%
- width-33	33.3333%
- width-50	50%
- width-67	66.6666%
- width-75	75%
- width-80	80%
- width-90	90%

用`offset`属性来设置列偏移（例如：`offset-25`）

## [HideWhen](http://ionicframework.com/docs/v2/api/components/show-hide-when/HideWhen/)

HideWhen用来设置某个平台或者某个屏幕方向时显示的元素。

```
<div hideWhen="android">
 I am hidden on Android!
</div>

<div hideWhen="ios">
 I am hidden on iOS!
</div>

<div hideWhen="android,ios">
 I am hidden on Android and iOS!
</div>

<div hideWhen="portrait">
 I am hidden on Portrait!
</div>

<div hideWhen="landscape">
 I am hidden on Landscape!
</div>
```

## [Icon](http://ionicframework.com/docs/v2/api/components/icon/Icon/)
Icon会自动识别平台并使用该平台的设计Icon。

```
<!-- 自动的识别平台并使用该平台的icon -->
<ion-icon name="star"></ion-icon>

<!-- 手动设置ios和android平台的图标 -->
<ion-icon ios="ios-home" md="md-home"></ion-icon>

<!-- 总是使用同一个图标，无论什么平台 -->
<ion-icon name="ios-clock"></ion-icon>
<ion-icon name="logo-twitter"></ion-icon>

<!-- 可变的name属性,myIcon是 -->
<ion-icon [name]="myIcon"></ion-icon>
```

### 属性

- name `string`
- ios `string`
- md `string`
- isActive `bool`

	设置该图标是否是活跃的图标。一般会用在tabbar中来将选中的tab图标置为活跃。

## [Id](http://ionicframework.com/docs/v2/api/components/app/Id/)
Id是一个应用程序中元素的唯一标识，可以通过它来获取到元素从而进行访问。

### 使用

```
<ion-checkbox id="myCheckbox"></ion-checkbox>
```

```
constructor(app: IonicApp) {
  this.app = app
}

ngAfterViewInit() {
  var checkbox = this.app.getComponent("myCheckbox");
  if (checkbox.checked) {
    console.log('checkbox is checked');
  }
}
```

通过IonicApp服务来访问元素。

注意：不建议使用Id，因为不能保证注册组件所在的页面是否已经被销毁或者离开当前视图。

## [InfiniteScroll](http://ionicframework.com/docs/v2/api/components/infinite-scroll/InfiniteScroll/)

当用户滚动到页面底部时，可以通过InfiniteScroll执行一个动作。

可以用来实现上拉加载。

### 使用方法

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

### Infinite Scroll Content

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

### 实例方法

#### `state()`

#### `complete()`
调用该方法来表示加载已经完成。

#### `enable(shouldEnable)`
调用该方法可以设置InfiniteScroll是否处于激活状态。当shouldEnable是`false`时，InfiniteScroll将被禁用。
- shouldEnable `boolean`

### 属性

- threshold `string`

	设置滚动触发的阙值。例如距离底部还有10%的时候触发事件。

### 输出事件

- infinite

## [Input](http://ionicframework.com/docs/v2/api/components/input/Input/)
`ion-input`拥有很多文本类型，例如：`text` `password` `email` `number` `search` `tel` 和 `url`。

## [IonicApp](http://ionicframework.com/docs/v2/api/components/app/IonicApp/)

### 实例方法

#### `setTitle(val)`
设置网页标题。

#### `isProd()`
返回是否生产模式。默认为`false`。可以在`@App`中的`config`中配置。

#### `isScrolling()`
返回布尔值。

#### `getComponent()`

获取给定键值的组件。

## [Item](http://ionicframework.com/docs/v2/api/components/item/Item/)
Item的使用有三种方法：

- 使用`<ion-item>`来创建一个不可点击文本。
- 使用 `<button ion-item>`。通常这个元素会有一个(click)处理程序
- 使用`<a ion-item>`当项目需要包含一个链接。

## [ItemSliding](http://ionicframework.com/docs/v2/api/components/item/ItemSliding/)
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

## [Keyboard](http://ionicframework.com/docs/v2/api/util/Keyboard/)
Keyboard允许你使用ionic键盘插件提供的键盘事件。

```
export class MyClass{
 constructor(keyboard: Keyboard){
   this.keyboard = keyboard;
 }
}
```

### 实例方法

- `isOpen()`

	检查键盘是否打开，返回一个boolean

- `onClose(callback)`

	当键盘被关闭时回调一个callback
	返回callback

- `close()`

	关闭键盘

## [List](http://ionicframework.com/docs/v2/api/components/list/List/)
### 实例方法
#### `enableSlidingItems(shouldEnable)`
是否开启滑动。

#### closeSlidingItems()
关闭滑动作

## [LocalStorage](http://ionicframework.com/docs/v2/api/platform/storage/LocalStorage/)

LocalStorage的储存引擎使用浏览器的本地储存系统储存键值对。

它只应用于临时储存的数据。
为保证长期的储存，请使用sqlstorage引擎将数据储存在一个文件。

```
import {Page, Storage, LocalStorage} from 'ionic-angular';
@Page({
  template: `<ion-content></ion-content>`
});
export class MyClass{
 constructor(){
   this.local = new Storage(LocalStorage);
   this.local.set('didTutorial', true);
 }
}
```

### 实例方法
#### `get(key)`
通过键名来访问LocalStorage中储存的值。

#### `set(key,value)`
通过键值对储存到LocalStorage

#### `remove(key)`
删除LocalStorage中储存的键值对

#### `clear()`

## [Menu](http://ionicframework.com/docs/v2/api/components/menu/Menu/)

Menu是一个侧滑菜单。

### 使用方法

Menu必须指定一个参考的`content`。

```
<ion-menu [content]="mycontent">
  <ion-content>
    <ion-list>
    ...
    </ion-list>
  </ion-content>
</ion-menu>

<ion-nav #mycontent [root]="rootPage"></ion-nav>
```
默认情况下菜单在左边滑动，你也可以使用`side`属性来让它从右边滑出。

```
<ion-menu side="right" [content]="mycontent">...</ion-menu>

```
如果你只是想简单的使用menu那么你可以使用`menuToggle` `menuClose`来控制menu的滑出和收回。

```
<button ion-item menuClose="leftMenu" detail-none>
        Close Menu
</button>
  <button menuToggle>
    <ion-icon name='menu'></ion-icon>
  </button>
```

如果你有多个menu从同一边滑出，你可以通过id来控制。

```
<ion-menu id="authenticated" side="left" [content]="mycontent">...</ion-menu>
<ion-menu id="unauthenticated" side="left" [content]="mycontent">...</ion-menu>
<ion-nav #mycontent [root]="rootPage"></ion-nav>
```

```
enableAuthenticatedMenu() {
  this.menu.enable(true, 'authenticated');
  this.menu.enable(false, 'unauthenticated');
}
```
注意：如果你只有一个menu那么请不用使用id控制。尽量避免使用id。

### Menu Types

menu可以设置显示的类型。

- overlay是传统的MD设计
- reveal是传统的ios设计

默认情况下，它们将自动使用当前平台的类型。

注：原文中还提到了一个`push`，我试过后发现和`reveal`是一样的，而且文章中也没有对`push`进行过多的解释。

### 实例方法
#### `open()`
打开菜单。返回一个`Promise`,当菜单被完全打开时，你可以执行一个事件。

#### `close(menuId)`

如果menuId为空，那么将关闭所有打开的菜单，如果menuId被设置，那么将关闭指定的菜单。返回一个`Promise`

#### `toggle(menuId)`
菜单开关。如果菜单当前关闭，那么将打开，如果菜单当前打开，将被关闭。
返回一个`Promise`。

#### `enable(menuId)`
当你有多个menu的时候，用于启用或禁用menu。当你启用一个menu那么同方向的其他menu将被禁用。
返回一个menu实例。

#### `swipeEnable(shouldEnable,menuId)`

#### `isOpen()`
返回一个布尔值来表示menu是否处于打开状态

#### `isEnabled`
返回一个布尔值来表示menu是否被启用

#### `get(menuId)`
返回一个menu实例，如果menuId的menu没有找到，那么将会返回`null`

#### `getMenus()`
返回menu实例数组

## [MenuClose](http://ionicframework.com/docs/v2/api/components/menu/MenuClose/)

该指令可以放在任何按钮，自动的关闭打开的菜单。

## [MenuToggle](http://ionicframework.com/docs/v2/api/components/menu/MenuToggle/)

该指令可以放在任何按钮，自动的开关menu。

## [Modals](http://ionicframework.com/docs/v2/api/components/modal/Modal/)

Modals是一个当前页面上的内容窗口。通常它是用来做选择或者编辑一个项目。

### 使用方法

```
import {Page, Modal, NavController, NavParams} from 'ionic-angular';

@Page(...)
class HomePage {

 constructor(nav: NavController) {
   this.nav = nav;
 }

 presentProfileModal() {
   let profileModal = Modal.create(Profile, { userId: 8675309 });
   this.nav.present(profileModal);
 }

}

@Page(...)
class Profile {

 constructor(params: NavParams) {
   console.log('UserId', params.get('userId'));
 }

}

```

### 静态方法
#### create(componentType,data)

- componentType `any`

	Modal类

- data `object`

	传给Modal的数据

### 实例方法
注明：本实例方法在当前英文文档中没有。

#### `onDismiss(call)`
当Modal被销毁的时候执行的回调函数。
call是一个回调函数。

### 例子

```
import {IonicApp, Modal, Platform, NavController, NavParams, Page, ViewController} from 'ionic-angular';



@Page({
  templateUrl: './build/pages/modals/basic/template.html'
})
export class BasicPage {
  constructor(public nav: NavController) { }

  openModal(characterNum) {
    let modal = Modal.create(ModalsContentPage,{charNum:1});
    this.nav.present(modal);
    modal.onDismiss(data=>{console.log(data)});
  }
}

@Page({
  templateUrl: './build/pages/modals/basic/modal-content.html'
})
class ModalsContentPage {
  character;

  constructor(
      public platform: Platform,
      public params: NavParams,
      public viewCtrl: ViewController
  ) {
    this.character = this.params.get('charNum');
  }

  dismiss() {
    this.viewCtrl.dismiss({a:1,b:2});
  }
}

```

## Nav
这是一个基本的导航控制器。

### 使用方法
```
import {GettingStartedPage} from 'getting-started';
@App({
  template: `<ion-nav [root]="rootPage"></ion-nav>`
})
class MyApp {
  constructor(){
    this.rootPage = GettingStartedPage;
  }
}

```

### Back navigation

`swipeBackEnabled`用来控制滑动返回。

```
<ion-nav swipeBackEnabled="false" [root]="rootPage"></ion-nav>

```
下图是一个App的架构

		                          +-------+
		                          |  App  |
		                          +---+---+
		                          <ion-app>
		                              |
		                 +------------+-------------+
		                 |   Ionic Nav Controller   |
		                 +------------+-------------+
		                          <ion-nav>
		                              |
		                              |
		            Page 3  +--------------------+                     LoginPage
		          Page 2  +--------------------+ |
		        Page 1  +--------------------+ | |              +--------------------+
		                | | Header           |<-----------------|       Login        |
		                +--------------------+ | |              +--------------------+
		                | | |                | | |              | Username:          |
		                | | |                | | |              | Password:          |
		                | | |  Page 3 is     | | |              |                    |
		                | | |  only content  | | |              |                    |
		                | | |                |<-----------------|                    |
		                | | |                | | |              |                    |
		                | | |                | | |              |                    |
		                | +------------------|-+ |              |                    |
		                | | Footer           |-|-+              |                    |
		                | +------------------|-+                |                    |
		                +--------------------+                  +--------------------+

		          +--------------------+    +--------------------+    +--------------------+
		          | Header             |    | Content            |    | Content            |
		          +--------------------+    |                    |    |                    |
		          | Content            |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    +--------------------+    |                    |
		          |                    |    | Footer             |    |                    |
		          +--------------------+    +--------------------+    +--------------------+



### 输入属性

- root `Page`

	当前打开的页面。

- swipeBackEnabled `boolean`

	是否开启滑动返回


## Navbar

### 输入属性

- hideBackButton `boolean`

	是否隐藏回退键。

## NavController

### 注入NavController

```
class MyComponent {
  constructor(nav: NavController) {
    this.nav = nav;
  }
}
```

### 页面展示

页面创建可以使用`@Page`装饰器。

当页面被添加到navigation栈的时候，页面就被展示了，使用`push()`方法。

页面销毁时将从navigation栈中移除（使用`pop()`或者`setRoot()`）。

### 生命周期

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

### 实例方法

#### `setRoot(page,params,opts)`

设置当前navigation栈的根节点

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|page|Type|页面的类型|
|params|object|传递到下一个视图的参数|
|opts|object|过渡选项|
返回：`Promise`

#### `setPages(pages,opts)`

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

#### `push(page,params,opts)`

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|page|Type|页面的类型|
|params|object|传递到下一个视图的参数|
|opts|object|过渡选项|

返回：`Promise`

#### `present(enteringView,opts)`

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

#### `insert(insertIndex,page,params,opts)`

插入一个视图到navigation栈。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| insertIndex | number | 插入的索引 |
|page|Type|页面的类型|
|params|object|传递到下一个视图的参数|
|opts|object|过渡选项|
返回：`Promise`

#### `insertPages(insertIndex,insertPages,opts)`

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
| insertIndex | number | 插入的索引 |
| insertPages |array<Type>|页面类型和参数组成的数组|
|opts|object|过渡选项|
返回：`Promise`

#### `pop(opts)`

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

#### `popToRoot(opts)`

直接跳转到根导航，不管在navigite栈中有多少视图。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|opts|object|过渡选项|

#### `popTo(view,opts)`

将当前视图到该视图的历史记录弹出，并跳转到指定视图。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|view|ViewController|
|opts|object|过渡选项|

#### `remove(startIndex,removeCount,opts)`

删除栈里指定索引段的元素。

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|startIndex|number|从栈中删除页面的起始索引，默认为最后一页的索引|
|removeCount|number|从栈中删除多少个页面，默认为1|
|opts|object|过渡选项|

返回一个`Promise`

#### `canSwipeBack()`

返回一个布尔值，来表示当前是否支持滑动返回

#### `canGoBack()`
返回一个布尔值，来表示是否还有可返回的页面

#### `getByIndex(index)`

返回指定索引的组件

#### `getActive()`

返回当前活动页面的视图控制器

#### `isActive(view)`

返回一个布尔值，来表示该视图是否是当前活动页面。

#### `getPrevious(view)`

返回指定页面的视图控制器

#### `first()`

返回当前栈中第一个的视图控制器

#### `last()`

返回当前栈中最后一个的视图控制器

#### `indexOf(view)`

返回某个视图在栈中的索引

#### `length()`

返回栈的长度。

#### `rootNav()`

返回`NavController`

## NavParams

类似于在Ionic V1版本中的`$stateParams`用来在页面中传递数据。

```
export class MyClass{
 constructor(params: NavParams){
   this.params = params;
   // userParams is an object we have in our nav-parameters
   this.params.get('userParams');
 }
}
```

### 实例方法

#### `data()`

#### `get(parameter)`

- parameter `string`

	是数据中键值对中的键名。


## NavPop
返回上一页的指令

```
<ion-content>
 <div block button nav-pop>go back</div>
</ion-content>

```

## NavPush
跳转到一个新的页面。

```
<button [navPush]="pushPage" [navParams]="params"></button>
```

## Option
`ion-option`是`ion-select`的子组件。

### 输入

- checked `boolean`

	是否被选中

- value `any`

	该选项的值

## Page
`@Page`装饰器包含`IONIC_DIRECTIVE`中所有的组件和指令以及Angular中的`CORS_DIRECTIVES`和 `FORM_DIRECTIVES`。所以你只需要将你自定义的指令和组件依赖进去就好。

### 使用方法

```
@Page({
  template: `
   <ion-content>
     I am a page!
   </ion-content>
  `
})
class MyPage {}
```
此时`@Page`已经帮你把那些指令注入进去了，所以你无需再次增加`directives`数组。

如果你需要自定义一个组件，而且需要依赖某个指令时，你需要手动加入。

```
import {IONIC_DIRECTIVES} from 'ionic-angular';
@Component({
  selector: 'my-component'
  template: `<div class="my-style">
                            <ion-checkbox></ion-checkbox>
                          </div>`,
  directives: [IONIC_DIRECTIVES]
})
class MyCustomCheckbox {}
```

或者你可以指定明确的指令来获取，并单独添加它。

```
import {Checkbox, Icon} from 'ionic-angular'
@Component({
  ...
  directives: [Checkbox, Icon]
})

```

然而，使用`IONIC_DIRECTIVES`不会产生额外的性能开销，所以，又有什么理由不用它呢。

## Platform

用来返回当前平台信息。它比ionic V1版本复杂，并不是单纯的返回一个平台信息，还有更多的信息，例如：设备系统，手机还是平板，移动app还是浏览器。

### 实例方法

#### `is(platformName)`

返回一个布尔值来表示当前平台是否是`platformName`。

注意：同一个环境下，当platformName不同时，可能不止有一个返回`true`。例如，Ipad可能返回`true`的platformName有：`mobile` `ios` `ipad` `tablet`等。

可能有的平台名有：

- android
- cordova
- core
- ios
- ipad
- iphone
- mobile
- mobileweb
- phablet
- tablet
- windows

```
import {Platform} from 'ionic-angular';

@Page({...})
export MyPage {
   constructor(platform: Platform) {
     if (platform.is('ios')) {
       // what ever you need to do
       // if the platform is ios
     }
   }
}
```

### `platforms()`

返回一个平台数组。

同一个环境下，可能会返回多个平台信息。

### `versions(platformName)`

返回一个包含系统相关信息的对象。

### `ready()`

返回一个`Promise`来表示设备是否准备好开始运行程序了。

### `setDir(dir)`

设置文字的排列方向。

- dir `string`

	ltr代表从左到右的排列
	rtl代表从右到左的排列

### `dir()`

返回文字排列方向。

### `isRTL()`
返回一个布尔值，来表示当前文本是否是从右到左排列的。

### `setLang(language)`

设置语言。

- language `string`

	`en-US` `en-GB` `ar` `de` `zh` `es-MX`等。

#### `lang()`

返回当前语言

## RadioButton

单选按钮必须包含在`<ion-list radio-group>`中，并且至少有两个。

### 使用方法

```
<ion-item>
  <ion-label>Radio Label</ion-label>
  <ion-radio value="radio-value"></ion-radio>
</ion-item>
```

### 输出事件

- select

	选择的时候执行的事件。

## RadioGroup

```
<ion-list radio-group [(ngModel)]="autoManufacturers">

  <ion-list-header>
    Auto Manufacturers
  </ion-list-header>

  <ion-item>
    <ion-label>Cord</ion-label>
    <ion-radio value="cord"></ion-radio>
  </ion-item>

  <ion-item>
    <ion-label>Duesenberg</ion-label>
    <ion-radio value="duesenberg"></ion-radio>
  </ion-item>

  <ion-item>
    <ion-label>Hudson</ion-label>
    <ion-radio value="hudson"></ion-radio>
  </ion-item>

  <ion-item>
    <ion-label>Packard</ion-label>
    <ion-radio value="packard"></ion-radio>
  </ion-item>

  <ion-item>
    <ion-label>Studebaker</ion-label>
    <ion-radio value="studebaker"></ion-radio>
  </ion-item>

</ion-list>
```

### 输出事件

- change

	在选择改变时执行的事件。

## [Refresher](http://ionicframework.com/docs/v2/api/components/refresher/Refresher/)

用来实现下拉刷新功能。

### 使用方法

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

### Refresher Content

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

### 实例方法

#### `state`

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

#### `startY`
返回用户开始下拉的Y坐标

#### `currentY`
返回当前触摸或鼠标事件的Y坐标。

#### `deltaY`
返回开始下拉的Y坐标距离当前触摸或鼠标事件的Y坐标的差值。

#### `progress`
0代表还没有到达某个距离，不触发刷新，1代表已经到达某个距离，松手触发刷新。

#### `complete()`
当你异步操作完成后，调用这个函数来关闭刷新动画，同时改变了状态。

#### `cancel()`
将状态从`refreshing`改变成`cancelling`

### 输入

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|pullMin|number|用户最小的下拉距离，默认为60|
|pullMax|number|用户下拉的最大距离，超过该距离后，自动进入刷新。默认最大距离为：pullmin+60。
|closeDuration|number|多少毫秒它需要关闭组件，默认为280|
| snapbackDuration|number|默认280|
|enabled|boolean|是否启用该组件|

### 输出事件

- `refresh`

	刷新事件。不要忘记在异步事件执行完成后调用`complete()`

- `pulling`

	当用户下拉的时候调用。

- `start`

	当用户开始下拉的时候调用。

## Scroll

```
<ion-scroll scrollX="true">
</ion-scroll>

<ion-scroll scrollY="true">
</ion-scroll>

<ion-scroll scrollX="true" scrollY="true">
</ion-scroll>

```

### 属性

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|scrollX|boolean|是否启用x轴滚动|
|scrollY|boolean|是否启用Y轴滚动|
|zoom|boolean|是否启动缩放|
|maxZoom|number|设置缩放的最大级别

## Searchbar

管理一个搜索栏，可以搜索或筛选项目的显示。

### 使用方法

```
<ion-searchbar
  [(ngModel)]="myInput"
  [hideCancelButton]="shouldHideCancel"
  (input)="onInput($event)"
  (cancel)="onCancel($event)">
</ion-searchbar>

```

### 输入属性


| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|cancelButtonText|string|设置取消按钮的文本值|
| hideCancelButton|boolean|是否隐藏取消按钮|
|debounce|number|每次键入字符等待触发事件的时间有多长，默认为250毫秒|
| placeholder|string|占位提示符|
|ngModel|any|搜索栏值的双向绑定|

### 输出事件

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

## Segment
Segment是一组按钮，允许用户和一组按钮进行交互，类似于标签页的功能。

### 使用方法

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

### 输出事件

- `change`

	当按钮改变时触发事件。

## Select
`ion-select`和html中的select有点相似。

### 单选

```
<ion-item>
  <ion-label>Gender</ion-label>
  <ion-select [(ngModel)]="gender">
    <ion-option value="f" checked="true">Female</ion-option>
    <ion-option value="m">Male</ion-option>
  </ion-select>
</ion-item>
```

### 多选

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

### Alert按钮

默认为`Cancel`和`OK`

```
<ion-select okText="Okay" cancelText="Dismiss">
  ...
</ion-select>

```

### Alert选项

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

### 输入

- multiple `boolean`

	是否可以接受多个选项

- disabled `boolean`

	组件是否被禁用

### 输出事件

- change

	当选项改变时触发

- cancel

	取消时触发

## ShowWhen
用来表示某平台或者某屏幕方向时时显示该元素。

```
<div showWhen="android">
 I am visible on Android!
</div>

<div showWhen="ios">
 I am visible on iOS!
</div>

<div showWhen="android,ios">
 I am visible on Android and iOS!
</div>

<div showWhen="portrait">
 I am visible on Portrait!
</div>

<div showWhen="landscape">
 I am visible on Landscape!
</div>

```

## Slides

Slides是基于Swiper.js实现的。

```
@Page({
 template: `
    <ion-slides pager (change)="onSlideChanged($event)" (move)="onSlideMove($event)">
     <ion-slide>
       <h3>Thank you for choosing the Awesome App!</h3>
       <p>
         The number one app for everything awesome.
       </p>
     </ion-slide>
     <ion-slide>
       <h3>Using Awesome</h3>
        <div id="list">
          <h5>Just three steps:</h5>
          <ol>
            <li>Be awesome</li>
            <li>Stay awesome</li>
            <li>There is no step 3</li>
          </ol>
        </div>
     </ion-slide>
     <ion-slide>
       <h3>Any questions?</h3>
     </ion-slide>
   </ion-slides>
   `
})

```

### 输入

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|pager|boolean|是否显示索引点|
| options|any|任何Slider需要配置的参数，可以参考[http://www.idangero.us/swiper/api/](http://www.idangero.us/swiper/api/)|
|zoom|number|该组件是否可以缩放|
|zoomDuration|number|缩放该组件需要多长时间|
|zoomMax|number|最大的缩放|

### 输出事件

- change

	当滑块变化的时候触发

- slideChangeStart

	当滑块开始更改时触发

- move

	当滑块移动时触发

## SqlStorage

SqlStorage采用SQLite查询。在文件系统中持久的储存数据，这是首选的储存引擎。引擎支持简单的键值对存储和完整的Sql查询。

```
let storage = new Storage(SqlStorage, options);
storage.set('name', 'Max');
storage.get('name').then((name) => {
});

// Sql storage also exposes the full engine underneath
storage.query('insert into projects(name, data) values("Cool Project", "blah")');
storage.query('select * from projects').then((resp) => {})

```

### 静态方法

#### `BACKUP_LOCAL()`
#### `BACKUP_LIBRARY()`
#### `BACKUP_DOCUMENTS()`

### 实例方法


#### `query(query,params)`

在数据库中执行SQL操作。

- query `string`

	sql字符串

- params `array`

返回一个`Promise`

#### `get(key)`

从数据库中获取给定的键名所对应的键值。

返回一个`Promise`

#### `set(key,value)`
从数据库中插入键值对

返回一个`Promise`
#### `remove(key)`

从数据库中删除键值对。

返回一个`Promise`

#### `clear()`

清空数据库

## Tab

底部的标签按钮

### 使用方法

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

### 输入

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|root|Page|设置根页面|
|rootParams|object|传递数据到该页面|
|tabTitle|string|页面标题
|tabIcon|string|页面图标|
|tabBadge|string|设置徽章
|tabBadgeStyle|string|设置徽章颜色

### 输出事件

- select

	选中时触发。

## Tabs
### 实例方法

#### `select(index)`

选中某个索引的选项卡

#### `getByIndex(index)`

返回一个和索引匹配的选项卡

#### `getSelected()`

返回当前选中的选项卡

### 输入
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|selectedIndex|number|第一次加载时默认选中的选项卡，如果不提供那么默认是0
| preloadTabs|boobean|是否预加载所有标签|
| tabbarIcons|string|这个属性是过时的，请使用TabBarLayout代替，设置图标的位置`top` `bottom` `left` `right` `hide`|
|tabbarLayout|string|设置tabbar的布局 `icon-top` `icon-left` `icon-right` `icon-bottom` `icon-hide` `title-hide`|
|tabbarPlacement|string|设置tabbar的位置：`top` `bottom`

### 输出事件

- change

	当标签页改变时触发

## TextArea

```
<ion-item>
  <ion-label stacked>Message</ion-label>
  <ion-textarea [(ngModel)]="msg"></ion-textarea>
</ion-item>

```

## Toggle

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

### 属性

- checked `boolean`

	是否打开

- disabled `boolean`

	是否禁用

### 输入

- checked
- disabled

### 输出事件

- change

	切换时触发

## Toolbar
Toolbar是一条在上面或者在下面的通用栏。

### 使用方法
```
<ion-toolbar>
  <ion-title>My Toolbar Title</ion-title>
</ion-toolbar>

<ion-toolbar>
  <ion-title>I'm a subheader</ion-title>
</ion-toolbar>

 <ion-content></ion-content>

<ion-toolbar position="bottom">
  <ion-title>I'm a subfooter</ion-title>
</ion-toolbar>

<ion-toolbar position="bottom">
  <ion-title>I'm a footer</ion-title>
</ion-toolbar>
```

### 属性

- position `any`

	设置toolbar的位置，默认是`top`

## ViewController

访问当前视图的功能和信息

### 使用方法

```
import {Page, ViewController} from 'ionic-angular';
@Page....
export class MyPage{
 constructor(viewCtrl: ViewController){
   this.viewCtrl = viewCtrl;
 }
}
```

### 实例方法

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
