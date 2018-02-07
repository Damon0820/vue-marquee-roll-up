# vue-marquee-roll-up
MarqueeUp向上轮播的跑马灯/RollNotice向上走的滚动公告/

> A vue plugin/component which is like a advertising board or marquee roll up。 一个vue的插件/组件，实现了类似广告牌向上滚动的效果滚动，或者说是向上滚动的跑马灯效果。

## Usage

# npm 下载
npm install marquee-roll-up --save-dev

# import 引入
import MarqueeRollUp from 'marquee-roll-up'

# use in vue component 在vue组件内使用

<template>
  <MarqueeRollUp speed="300" autoPlay="5000" :marqueeList="list" 
  height="100" width="200" bg="#f99" color="#fff" fontSize="40"/>
</template>

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


# Params: props 可传属性参数

      // 	宽度（px）      
      width: {
        validator (val) {
          return regNumber.test(val)
        },
        default: 200
      },
      // 	高度（px）
      height: {
        validator (val) {
          return regNumber.test(val)
        },
        default: 38
      },
      // 	背景颜色
      bg: {
        type: String,
        default: '#BD9955'
      },
      // 	字体颜色
      color: {
        type: String,
        default: '#fff'
      },
      // fontSize (px)
      fontSize: {
        validator (val) {
          return regNumber.test(val)
        },
        default: 12
      },
      // 	自动播放时间（毫秒ms）
      autoplay: {
        validator (val) {
          return regNumber.test(val)
        },
        default: 3000
      },
      // 	切换速度（毫秒ms）
      speed: {
        validator (val) {
          return regNumber.test(val)
        },
        default: 500
      },
      marqueeList: {
        type: Array,
        default: function () {
          return [
            '测试数据1',
            '测试数据2',
            '测试数据3',
            '测试数据4',
            '测试数据5'
          ]
        }
      }

