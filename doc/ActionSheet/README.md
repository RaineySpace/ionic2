# [ActionSheet](http://ionicframework.com/docs/v2/api/components/action-sheet/ActionSheet/)
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

