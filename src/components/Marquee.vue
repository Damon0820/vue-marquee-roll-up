/**
 * Created by Damon on 2018/02/26
 * Description: 跑马灯 滚动公告 RollNotice
 * A vue plugin/component which is like a advertising board or marquee roll up。
 * 一个vue的插件/组件，实现了类似广告牌向上滚动的效果滚动，或者说是向上滚动的跑马灯效果。
 */

<template>
  <div class="scores-marquee flex-row">
    <div v-if="marqueeList.length > 0" class="marquee-all">
      <div class="marquee flex-row">
        <div class="marque-wrap" :style="stylesWrap">
          <div class="list"
              id="detail-marquee-list"
              :style="styles">

            <div v-for="(item, index) in marqueeList" :key="index" 
              :style="stylesItem"
              class="item">
              {{item}}
            </div>

            <!-- 最后一个元素和第一个相同 -->
            <div v-if="marqueeList.length > 0" 
              :style="stylesItem" 
              class="item">
              {{marqueeList[0]}}
            </div>

          </div>
        </div>
        <div class="tri" :style="stylesTri"></div>
      </div>
    </div>
  </div>
</template>

<script>
  const regNumber = /^\d+$/

  export default {
    components: {},
    data () {
      return {
        indexMq: 0,
        timer: null,
        // 运动
        styles: {
          top: 0,
          transitionDuration: 0
        },

        // wrap样式
        stylesWrap: {
          background: this.bg,
          width: this.width + 'px',
          height: this.height + 'px',
        },
        // item样式
        stylesItem: {
          height: this.height + 'px',
          lineHeight: this.height + 'px',
          color: this.color,
          fontSize: this.fontSize + 'px',
          background: this.bg
        },
        // 三角形
        stylesTri: {
          borderTop: `${this.height}px solid ${this.bg}`,
          borderRight: `${this.height}px solid transparent`
        }
      }
    },
    props: {
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
      // 	自动播放时间（毫秒）
      autoplay: {
        validator (val) {
          return regNumber.test(val)
        },
        default: 3000
      },
      // 	切换速度（毫秒）
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
    },
    computed: {
      lenMq () {
        return this.marqueeList ? this.marqueeList.length : 0
      }
    },
    methods: {
      setTop (speed, top) {
        this.styles.transitionDuration = speed + 'ms'
        this.styles.top = top + 'px'
      }
    },
    mounted () {
      // 当前新1个
      // 1.跑马灯无缝循环播放原理：轮播到最后一个的时候，轮播新1而不是老1。
      // 2.轮播到新1后，结束动画后，让老一瞬间就到新一的位置（此应用内联css实现，不得用class实现，因为动态添加class，class再获取样式需要一定时间）
      // 3.以下代码实现，只能往当前的indexMq后面添加数据。若往前传数据，对应的indexMq得加瞬间加到对应位置（处理比较复杂）
      this.timer = setInterval(() => {
        this.setTop(this.speed, -(++this.indexMq * this.height))
        if (this.indexMq >= this.lenMq) {
          // 若当前是新1(最後一個)，
          setTimeout(() => {
            // 瞬间回到老1（第一个）
            this.indexMq = 0
            this.setTop(0, 0)
          }, this.speed)
        }
      }, this.autoplay)
    },
    destroyed () {
      clearInterval(this.timer)
      this.timer = null
      this.indexMq = 0
    }
  }
</script>

<style scoped>
  .flex-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .scores-marquee {
  }

  .marque-wrap {
    overflow: hidden;
    position: relative;
  }

  .list {
    position: absolute;
    left: 0;
    top: 0;
  }

  .item {
    margin-left: 12px;
    
    overflow: hidden;
  }

  .tri {
    width: 0;
    height: 0;
    /* border-top: $marqueeHeight solid #BD9955; */
    /* border-right: $marqueeHeight solid transparent; */
  }
</style>

