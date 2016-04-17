# Slides

Slides是基于Swiper.js实现的。

```
@Page({
 template: `
    <ion-slides pager (change)="onSlideChanged($event)" (move)="onSlideMove($event)">
     <ion-slide>
       <h3>Thank you for choosing the Awesome App!</h3>
       <p>
         The number one app for everything awesome.
       </p>
     </ion-slide>
     <ion-slide>
       <h3>Using Awesome</h3>
        <div id="list">
          <h5>Just three steps:</h5>
          <ol>
            <li>Be awesome</li>
            <li>Stay awesome</li>
            <li>There is no step 3</li>
          </ol>
        </div>
     </ion-slide>
     <ion-slide>
       <h3>Any questions?</h3>
     </ion-slide>
   </ion-slides>
   `
})

```

## 输入

| 属性名称          | 类型           |描述                 |
| -------------    |:------------- |:-------------      |
|pager|boolean|是否显示索引点|
| options|any|任何Slider需要配置的参数，可以参考[http://www.idangero.us/swiper/api/](http://www.idangero.us/swiper/api/)|
|zoom|number|该组件是否可以缩放|
|zoomDuration|number|缩放该组件需要多长时间|
|zoomMax|number|最大的缩放|

## 输出事件

- change

	当滑块变化的时候触发

- slideChangeStart

	当滑块开始更改时触发

- move

	当滑块移动时触发

