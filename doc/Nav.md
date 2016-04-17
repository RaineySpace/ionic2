
# Nav
这是一个基本的导航控制器。

## 使用方法
```
import {GettingStartedPage} from 'getting-started';
@App({
  template: `<ion-nav [root]="rootPage"></ion-nav>`
})
class MyApp {
  constructor(){
    this.rootPage = GettingStartedPage;
  }
}

```

## Back navigation

`swipeBackEnabled`用来控制滑动返回。

```
<ion-nav swipeBackEnabled="false" [root]="rootPage"></ion-nav>

```
下图是一个App的架构

		                          +-------+
		                          |  App  |
		                          +---+---+
		                          <ion-app>
		                              |
		                 +------------+-------------+
		                 |   Ionic Nav Controller   |
		                 +------------+-------------+
		                          <ion-nav>
		                              |
		                              |
		            Page 3  +--------------------+                     LoginPage
		          Page 2  +--------------------+ |
		        Page 1  +--------------------+ | |              +--------------------+
		                | | Header           |<-----------------|       Login        |
		                +--------------------+ | |              +--------------------+
		                | | |                | | |              | Username:          |
		                | | |                | | |              | Password:          |
		                | | |  Page 3 is     | | |              |                    |
		                | | |  only content  | | |              |                    |
		                | | |                |<-----------------|                    |
		                | | |                | | |              |                    |
		                | | |                | | |              |                    |
		                | +------------------|-+ |              |                    |
		                | | Footer           |-|-+              |                    |
		                | +------------------|-+                |                    |
		                +--------------------+                  +--------------------+

		          +--------------------+    +--------------------+    +--------------------+
		          | Header             |    | Content            |    | Content            |
		          +--------------------+    |                    |    |                    |
		          | Content            |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    |                    |    |                    |
		          |                    |    +--------------------+    |                    |
		          |                    |    | Footer             |    |                    |
		          +--------------------+    +--------------------+    +--------------------+



## 输入属性

- root `Page`

	当前打开的页面。

- swipeBackEnabled `boolean`

	是否开启滑动返回

