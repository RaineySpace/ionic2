# Tabs
## 实例方法

### `select(index)`

选中某个索引的选项卡

### `getByIndex(index)`

返回一个和索引匹配的选项卡

### `getSelected()`

返回当前选中的选项卡

## 输入
| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|selectedIndex|number|第一次加载时默认选中的选项卡，如果不提供那么默认是0
| preloadTabs|boobean|是否预加载所有标签|
| tabbarIcons|string|这个属性是过时的，请使用TabBarLayout代替，设置图标的位置`top` `bottom` `left` `right` `hide`|
|tabbarLayout|string|设置tabbar的布局 `icon-top` `icon-left` `icon-right` `icon-bottom` `icon-hide` `title-hide`|
|tabbarPlacement|string|设置tabbar的位置：`top` `bottom`

## 输出事件

- change

	当标签页改变时触发