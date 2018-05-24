<template>
  <div class="swiper">
    <ul class="item-wrap" :style="{width: contentWidth}">
      <transition-group name="fade">
        <li class="item" v-for="(img, index) in imgs" v-show="index===mark"  :key="index">
          <img :src="img" alt="">
        </li>
      </transition-group>
    </ul>
    <div class="dots">
      <a v-for="(img, index) in imgs" href="#" :key="img" @click.prevent="change(index)" :class="[index===mark? 'dot-current': 'dot-default', 'dot']"></a>
    </div>
    <a class="btn btn-pre" href="#" @click="pre"> &lt; </a>
    <a class="btn btn-next" href="#" @click="next"> &gt; </a>
  </div>
</template>

<script>
export default {
  name: 'Swiper',
  data() {
    return {
      mark: 0,
      timer: {}
    }
  },
  props: {
    imgs: {
      type: Array,
      required: true
    },
    interval: {
      type: [Number, String],
      default: 3000
    }
  },
  computed: {
    contentWidth() {
      return `${this.imgs.length * 100}%`
    }
  },
  created() {
    this.autoPlay()
  },
  methods: {
    autoPlay() {
      this.timer = setInterval(() => {
        if (this.mark < this.imgs.length - 1) {
          this.mark++
        } else {
          this.mark = 0
        }
      }, Number(this.interval))
    },
    change(index) {
      clearInterval(this.timer)
      this.mark = index;
      this.autoPlay()
    },
    pre() {
      clearInterval(this.timer)
      if (this.mark === 0) {
        this.mark = this.imgs.length - 1
      } else {
        this.mark--
      }
      this.autoPlay()
    },
    next() {
      clearInterval(this.timer)
      if (this.mark < this.imgs.length - 1) {
        this.mark++
      } else {
        this.mark = 0
      }
      this.autoPlay()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{
  margin: 0;
  padding: 0;
}
.swiper{
  width: 100%;
  height: 100%;
  position: relative;
  overflow: hidden;
}
.item-wrap{
  position: relative;
}
.item{
  list-style: none;
  opacity: 1;
  position: absolute;
  top: 0;
  left: 0;
}
.dots{
  position: absolute;
  bottom: 20px;
  left: 0;
  width: 730px;
  height: 20px;
  text-align: center;
}
.dot{
  display: inline-block;
  width: 20px;
  height: 20px;
  background: url('../../static/banner.png') no-repeat;
  background-position: 3px -343px;
  cursor: pointer;
  outline: none;
}
.dot-current{
  background-position: -16px -343px;
}
.dot-default{
  background-position: 3px -343px;
}
.btn{
  position: absolute;
  display: block;
  position: absolute;
  top: 50%;
  margin-top: -31px;
  width: 37px;
  height: 63px;
  text-indent: -9999px;
  background: url('../../static/banner.png') no-repeat;
}
.btn-pre{
  left: 10px;
  background-position: 0 -360px;
}
.btn-pre:hover{
  background-position: 0 -430px;
}
.btn-next{
  right: 10px;
  background-position: 0 -508px;
}
.btn-next:hover{
  background-position: 0 -578px;
}
.fade-enter, .fade-leave-active {
  opacity: 0;
}
.fade-leave-active, .fade-enter-active {
  transition: opacity 800ms;
}
</style>
