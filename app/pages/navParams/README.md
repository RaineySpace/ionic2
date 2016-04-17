# NavParams

类似于在Ionic V1版本中的`$stateParams`用来在页面中传递数据。

```
export class MyClass{
 constructor(params: NavParams){
   this.params = params;
   // userParams is an object we have in our nav-parameters
   this.params.get('userParams');
 }
}
```

## 实例方法

### `data()`

### `get(parameter)`

- parameter `string`

	是数据中键值对中的键名。

