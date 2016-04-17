
# Page
`@Page`装饰器包含`IONIC_DIRECTIVE`中所有的组件和指令以及Angular中的`CORS_DIRECTIVES`和 `FORM_DIRECTIVES`。所以你只需要将你自定义的指令和组件依赖进去就好。

## 使用方法

```
@Page({
  template: `
   <ion-content>
     I am a page!
   </ion-content>
  `
})
class MyPage {}
```
此时`@Page`已经帮你把那些指令注入进去了，所以你无需再次增加`directives`数组。

如果你需要自定义一个组件，而且需要依赖某个指令时，你需要手动加入。

```
import {IONIC_DIRECTIVES} from 'ionic-angular';
@Component({
  selector: 'my-component'
  template: `<div class="my-style">
                            <ion-checkbox></ion-checkbox>
                          </div>`,
  directives: [IONIC_DIRECTIVES]
})
class MyCustomCheckbox {}
```

或者你可以指定明确的指令来获取，并单独添加它。

```
import {Checkbox, Icon} from 'ionic-angular'
@Component({
  ...
  directives: [Checkbox, Icon]
})

```

然而，使用`IONIC_DIRECTIVES`不会产生额外的性能开销，所以，又有什么理由不用它呢。

