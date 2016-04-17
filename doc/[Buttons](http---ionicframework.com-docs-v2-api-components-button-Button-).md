
# [Buttons](http://ionicframework.com/docs/v2/api/components/button/Button/)
Button是ionic中的简单句子，可以显示文本、图标或者都显示。

## 属性

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

## Icon Buttons

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
