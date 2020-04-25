<template>
  <div class="box">
    <!-- 轮播图 -->
    <div class="indexHeader">
      <swiper indicator-dots="turs" autoplay="turs">
        <block v-for="(item,index) in imgUrls" :key="index">
          <swiper-item>
            <img :src="item" alt />
          </swiper-item>
        </block>
      </swiper>
    </div>
    <!-- 、轮播图 -->

    <!-- 导航块 -->
    <div class="indexContent">
      <div class="indexContent_1" @click="JumpActivity">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/da11db5345/home_1.jpg"
          alt
        />
        <p>活动</p>
      </div>
      <div class="indexContent_1" @click="JumpVolume1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/8156769438/home_2.jpg"
          alt
        />
        <p>问卷</p>
      </div>
      <div class="indexContent_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/1024x756/filters:focal(610x450:611x451):quality(100)/f/11/1220x900/cdab32ecc2/home_3.jpg"
          alt
        />
        <p>活动</p>
      </div>
      <div class="indexContent_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/a8a87f5dcf/home_4.jpg"
          alt
        />
        <p>活动</p>
      </div>
    </div>
    <!-- /导航块 -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      imgUrls: [
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/newsPicture/05558951-de60-49fb-b674-dd906c8897a6",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/coursePicture/0fbcfdf7-0040-4692-8f84-78bb21f3395d",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/management-school-picture/7683b32e-4e44-4b2f-9c03-c21f34320870"
      ]
    };
  },

  components: {},

  methods: {
    JumpActivity() {
      mpvue.navigateTo({ url: "../activity/main" });
    },
    JumpVolume1() {
      mpvue.navigateTo({ url: "../volume/volume1/main" });
    }
  },

  created() {
    // let app = getApp()
  },
  mounted() {}
};
</script>

<style scoped>
.box {
  background-color: rgb(245, 245, 245);
  height: 1334rpx;
}
.indexHeader img {
  width: 828rpx;
}
.indexContent {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  margin: 20rpx 0;
}
.indexContent_1 {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: white;
  margin-top: 10rpx;
  padding: 10rpx;
}
.indexContent_1 img {
  margin: 5rpx 0 10rpx 0;
  height: 300rpx;
  width: 300rpx;
}
</style>
