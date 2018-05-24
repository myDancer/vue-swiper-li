## vue-swiper-lj

*   基于 Vue2.0 开发，基本满足大部分功能
*   轻量、高性能轮播插件。目前支持自动轮播、无限轮播、手势轮播

## demo

![效果](./preview.gif)

🎉 觉得好用给一个 star 哦~ 🎉

## Install

```javascript
npm i vue-swiper-lj --save
cnpm i vue-swiper-lj --save  //淘宝镜像
```

## Usage

```javascript
import { Swiper } from 'vue-swiper-lj';
data() {
  return{
    imgs: [
        'http://p1.music.126.net/JBy1FYoB8QoTPj7LGsGcZQ==/109951163312508936.jpg',
        'http://p1.music.126.net/7mfBQD7u1lZR0eiqb8bTAA==/109951163312449573.jpg',
        'http://p1.music.126.net/UO5gvUIk9RZL78u5ZsoIBA==/109951163312707065.jpg'
    ]
  }
},
components: {
    Swiper
}

//异步加载轮播图的情况
  <Swiper :imgs="imgs" :interval="3000">
  </Swiper>

```

## API

| 属性          | 说明                     | 默认 |
| ------------- | ------------------------ | ---- |
| imgs      | 图片数组             | 必须 |
| interval      | 每两次隔多久滚动一次     | 3000 |

```javascript
```

