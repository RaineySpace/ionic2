# [Alert](http://ionicframework.com/docs/v2/api/components/alert/Alert/)

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
