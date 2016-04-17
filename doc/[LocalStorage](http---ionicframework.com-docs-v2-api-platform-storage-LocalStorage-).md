# [LocalStorage](http://ionicframework.com/docs/v2/api/platform/storage/LocalStorage/)

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

## 实例方法
### `get(key)`
通过键名来访问LocalStorage中储存的值。

### `set(key,value)`
通过键值对储存到LocalStorage

#### `remove(key)`
删除LocalStorage中储存的键值对

### `clear()`

