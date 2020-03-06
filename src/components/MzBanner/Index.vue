<template>
  <div class="swiper-container mz-banner">
    <div class="swiper-wrapper">
      <div class="swiper-slide"
        v-for="item in bannerList"
        :key="item.id">
        <img :src="item.imgUrl" alt="">
      </div>
    </div>
    <!-- 如果需要分页器 -->
    <div class="swiper-pagination"></div>

  </div>
</template>

<script>
import axios from 'axios';
export default {
  data: function () {
    return {
      bannerList: [],
      mySwiper: null
    }
  },
  methods: {
    initSwiper () {
      /* eslint-disable */
      this.mySwiper  = new Swiper(".swiper-container", {
        loop: true, // 循环模式选项
        autoplay: {
          delay: 2000,
          stopOnLastSlide: false,
          disableOnInteraction: true,
        },
        // 如果需要分页器
        pagination: {
          el: ".swiper-pagination"
        },
      });
    }
  },
  created () {
    axios.get('http://localhost:8081/page')
      .then((res) => {
        console.log(res)
        const data = res.data;
        this.bannerList = data.data;
        this.$nextTick(() => {
          this.initSwiper();
        })
      })
  },
  mounted () {
    
  }
};
</script>

<style lang="less">
.mz-banner {
  height: 210px;
}
img {
  width: 100%;
}
</style>
