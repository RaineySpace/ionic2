# [Modals](http://ionicframework.com/docs/v2/api/components/modal/Modal/)

Modals是一个当前页面上的内容窗口。通常它是用来做选择或者编辑一个项目。

## 使用方法

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

## 静态方法
### create(componentType,data)

- componentType `any`

	Modal类

- data `object`

	传给Modal的数据

## 实例方法
注明：本实例方法在当前英文文档中没有。

### `onDismiss(call)`
当Modal被销毁的时候执行的回调函数。
call是一个回调函数。

## 例子

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
