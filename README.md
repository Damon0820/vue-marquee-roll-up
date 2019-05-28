# vue-marquee-roll-up
vue插件：向上轮播的跑马灯/向上走的滚动公告。vue's plugin:  a marquee which roll up. mobile-friendly

> A vue plugin/component which is like a advertising board or marquee roll up。 一个vue的插件/组件，实现了类似广告牌向上滚动的效果滚动，或者说是向上滚动的跑马灯效果。

## show result 效果展示

![Damon风](https://github.com/Damon0820/vue-marquee-roll-up/blob/master/static/img/show2.gif "Damon风")
</br>[Damon风的blog地址](https://www.cnblogs.com/damonFeng/)

## Installation

### npm
```
npm install marquee-roll-up --save
````

### import
````
import MarqueeRollUp from 'marquee-roll-up'
````

### Usage

``` html
<template>
  <div>
    <MarqueeRollUp 
      :marqueeList="list"
      speed="300" 
      autoPlay="5000" 
      height="100" 
      width="200" 
      bg="#f99" 
      color="#fff" 
      fontSize="40">
    <MarqueeRollUp/>
  </div>
</template>
```
``` javascript
<script>
  import MarqueeRollUp from 'marquee-roll-up'
  export default {
    components: { MarqueeRollUp },
    data () {
      return {
        list: [
          'info item0',
          'info item1',
          'info item2',
          'info item3'
        ]
      }
    }
  }
</script>
```

### Props 参数

      * marqueeList:  [Array]                              跑马灯所跑的信息 the data of the marquee
      * width,height: (px) [Number/String] && match(/\d+/) 跑马灯的宽度和高度 the maximum width and height of the preview container。 width-default: 200 height-default: 38
      * bg:           (color) [String]                     跑马灯的背景颜色 the backgroundColor of the preview container。 default: '#BD9955'
      * color:        (color) [String]                     跑马灯的内容区字体颜色 the color of the font。 default: '#fff'
      * fontSize:     (px) [Number/String] && match(/\d+/) 跑马灯的字体大小 the fontSize of the font。 default: 12
      * autoplay:     (ms) [Number/String] && match(/\d+/) 轮播间隔时间 the autoplay time。 default: 3000
      * speed:        (ms) [Number/String] && match(/\d+/) 轮播动画的速度 the speed of animation。 default: 500


### show2 上面使用事例的配置参数展示图 VS 默认样式展示图。the show of above example with personal options VS the show with default options
![Damon风](https://github.com/Damon0820/vue-marquee-roll-up/blob/master/static/img/show1.png "Damon风")
