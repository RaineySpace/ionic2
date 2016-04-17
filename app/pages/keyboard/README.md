
# [Keyboard](http://ionicframework.com/docs/v2/api/util/Keyboard/)
Keyboard允许你使用ionic键盘插件提供的键盘事件。

```
export class MyClass{
 constructor(keyboard: Keyboard){
   this.keyboard = keyboard;
 }
}
```

## 实例方法

- `isOpen()`

	检查键盘是否打开，返回一个boolean

- `onClose(callback)`

	当键盘被关闭时回调一个callback
	返回callback

- `close()`

	关闭键盘
