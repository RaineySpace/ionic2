# [Menu](http://ionicframework.com/docs/v2/api/components/menu/Menu/)

Menu是一个侧滑菜单。

## 使用方法

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

## Menu Types

menu可以设置显示的类型。

- overlay是传统的MD设计
- reveal是传统的ios设计

默认情况下，它们将自动使用当前平台的类型。

注：原文中还提到了一个`push`，我试过后发现和`reveal`是一样的，而且文章中也没有对`push`进行过多的解释。

## 实例方法
### `open()`
打开菜单。返回一个`Promise`,当菜单被完全打开时，你可以执行一个事件。

### `close(menuId)`

如果menuId为空，那么将关闭所有打开的菜单，如果menuId被设置，那么将关闭指定的菜单。返回一个`Promise`

### `toggle(menuId)`
菜单开关。如果菜单当前关闭，那么将打开，如果菜单当前打开，将被关闭。
返回一个`Promise`。

### `enable(menuId)`
当你有多个menu的时候，用于启用或禁用menu。当你启用一个menu那么同方向的其他menu将被禁用。
返回一个menu实例。

### `swipeEnable(shouldEnable,menuId)`

### `isOpen()`
返回一个布尔值来表示menu是否处于打开状态

### `isEnabled`
返回一个布尔值来表示menu是否被启用

### `get(menuId)`
返回一个menu实例，如果menuId的menu没有找到，那么将会返回`null`

### `getMenus()`
返回menu实例数组
