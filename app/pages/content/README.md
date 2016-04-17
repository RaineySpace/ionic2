
# [Content](http://ionicframework.com/docs/v2/api/components/content/Content/)
Content组件提供了易于使用的方法来控制滚动，同时可以和其他组件配合实现下拉刷新和上拉加载的功能。

## 实例方法

### `onScrollElementTransitionEnd()`

### `scrollTo(x,y,duration,tolerance)`
滚动到具体的坐标

- x `number`

	x轴距离

- y `number`

	y轴距离

- duration `number`

	滚动动画的持续时间

- tolerance `TODO`


此函数执行完毕后，返回一个`Promise`

### `scrollToTop()`

滚动到顶部，执行完毕后返回一个`Promise`

### `getContentDimensions()`
获取content的尺寸

