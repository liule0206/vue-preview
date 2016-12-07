<template>
  <transition-group tag="div">
    <div v-show="show" :key="0" class="preview_transparent">
      <div class="preview" @touchstart="movstart" @touchmove="mov" @touchend="movend" @click="close">
        <ul :style="[ulWidth, styleObj]" :left="left">
          <li v-for="item in options" :style="liWidth">
            <div>
              <img :src="item.imgInfo" alt="">
            </div>
          </li>
        </ul>
      </div>
    </div>
  </transition-group>
</template>

<script>
  const sw = document.body.scrollWidth
  export default {
    name: 'c-preview',
    props: {
      show: {
        type: Boolean
      },
      options: {
        type: Array,
        require: true,
        default: []
      },
      dis: {
        type: Number,
        default: 0
      }
    },
    data() {
      return {
        start: 0,
        end: 0,
        styleObj: {
          'transform': 'translate3d(0,0,0)',
          'transition': '400ms'
        },
        left: 0,
        cur: 0
      }
    },
    mounted() {
      this.cur = this.dis || 0
      const postion = this.cur * sw
      this.styleObj.transform = `translate3d(-${postion}px,0,0)`
      this.left = `-${postion}px`
    },
    computed: {
      ulWidth() {
        return {
          width: `${sw * this.options.length}px`
        }
      },
      liWidth() {
        return `width: ${sw}px`
      }
    },
    methods: {
      movstart(e) {
        this.start = e.targetTouches[0].clientX
        this.end = e.targetTouches[0].clientX
      },
      mov(e) {
        this.end = e.targetTouches[0].clientX
      },
      movend(e) {
        const pos = this.start - this.end
        if (Math.abs(pos) > 20) {
          if (pos > 0 && this.cur < this.options.length - 1) { // 向右滑动
            this.cur = this.cur + 1
            const postion = this.cur * sw
            this.styleObj.transform = `translate3d(-${postion}px,0,0)`
            this.left = `-${postion}px`
          }
          if (pos < 0 && this.cur > 0) { // 向左滑动
            this.cur = this.cur - 1
            const postion = this.cur * sw
            this.styleObj.transform = `translate3d(-${postion}px,0,0)`
            this.left = `-${postion}px`
          }
        }
      },
      close() {
        this.$emit('on-close')
      }
    }
  }

</script>

<style src="./preview.css"></style>
