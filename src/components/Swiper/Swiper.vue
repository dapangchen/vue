<template>
  <div>
    <group-title>THX to: https://github.com/wechatui/swiper</group-title>
    <group-title>list模式下，默认高度为180px, 如果设置aspect-ratio会根据宽度自动计算高度</group-title>
    <swiper :list="demo01_list" v-model="demo01_index" @on-index-change="demo01_onIndexChange"></swiper>
    <p class="copyright">Image Source: http://www.gratisography.com/</p>
    <p>current index: {{demo01_index}}</p>
    <x-button @click.native="demo01_index = 0">go to 0</x-button>
    <x-button @click.native="demo01_index = 1">go to 1</x-button>
    <x-button @click.native="demo01_index = 2">go to 2</x-button>
  </div>
</template>

<script>
import { Swiper, GroupTitle, SwiperItem, XButton } from "vux";

const baseList = [
  {
    url: "javascript:",
    img: "https://ww1.sinaimg.cn/large/663d3650gy1fq66vvsr72j20p00gogo2.jpg",
    title: "送你一朵fua"
  },
  {
    url: "javascript:",
    img: "https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg",
    title: "送你一辆车"
  },
  {
    url: "javascript:",
    img: "https://static.vux.li/demo/5.jpg", // 404
    title: "送你一次旅行",
    fallbackImg:
      "https://ww1.sinaimg.cn/large/663d3650gy1fq66vw50iwj20ff0aaaci.jpg"
  }
];

const imgList = [
  "http://placeholder.qiniudn.com/800x300/FF3B3B/ffffff",
  "http://placeholder.qiniudn.com/800x300/FFEF7D/ffffff",
  "http://placeholder.qiniudn.com/800x300/8AEEB1/ffffff"
];

const urlList = baseList.map((item, index) => ({
  url: "http://m.baidu.com",
  img: item.img,
  fallbackImg: item.fallbackImg,
  title: `(可点击)${item.title}`
}));

const demoList = imgList.map((one, index) => ({
  url: "javascript:",
  img: one
}));

const only2ClickList = baseList.slice(0, 2).map(item => {
  item.url = "http://m.baidu.com";
  return item;
});

export default {
  components: {
    Swiper,
    SwiperItem,
    GroupTitle,
    XButton
  },
  ready() {},
  methods: {
    onSwiperItemIndexChange(index) {
      console.log("demo item change", index);
    },
    demo01_onIndexChange(index) {
      this.demo01_index = index;
    },
    demo05_onIndexChange(index) {
      this.demo05_index = index;
    },
    demo05_onLoad(id) {
      this.demo05_list = id === 1 ? baseList : demoList;
    },
    demo06_onIndexChange(index) {
      this.demo06_index = index;
    },
    demo07_onIndexChange(index) {
      this.demo07_index = index;
    }
  },
  data() {
    return {
      demo01_list: baseList,
      demo02_list: demoList,
      demo03_list: demoList,
      demo04_list: imgList,
      demo05_list: [],
      demo06_list: urlList,
      demo07_list: only2ClickList,
      demo01_index: 0,
      demo02_index: 1,
      demo05_index: 0,
      demo06_index: 0,
      demo07_index: 0,
      swiperItemIndex: 1
    };
  }
};
</script>

