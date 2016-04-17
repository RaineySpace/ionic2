# [Config](http://ionicframework.com/docs/v2/api/config/Config/)
用来配置整个应用程序。

## 属性

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

## 实例方法

### `get(key, fallbackValue)`

- key `string`

	config的键

- fallbackValue `any`

### `getBoolean(key)`

### `set(platform,key,value)`

- platform `string`

	"ios"或者"android"
