<template>
  <div>
    <!-- 轮播图 -->
    <div class="logsIndexHeader">
      <swiper indicator-dots="turs" autoplay="turs">
        <block v-for="(item,index) in imgUrls" :key="index">
          <swiper-item>
            <img :src="item" alt />
          </swiper-item>
        </block>
      </swiper>
    </div>
    <!-- /轮播图 -->

    <!-- 内容 -->
    <div class="logsIndexContent">
      <p>热门活动</p>
      <ul>
        <li @click="JumpAtcontent">
          <span class="span1">1</span>
          <span class="span2">内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容</span>
          <span class="span3">999</span>
          <span class="span4">
            <img
              src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=2592366594,1832501193&fm=26&gp=0.jpg"
              alt
            />
          </span>
        </li>
      </ul>
    </div>
    <!-- 、内容 -->

    <!-- fixed按钮 -->
    <div class="Jdsy" @click="JumPindex">首页</div>
    <!-- 、fixed按钮 -->
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      imgUrls: [
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/newsPicture/05558951-de60-49fb-b674-dd906c8897a6",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/coursePicture/0fbcfdf7-0040-4692-8f84-78bb21f3395d",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/management-school-picture/7683b32e-4e44-4b2f-9c03-c21f34320870"
      ]
    };
  },
  methods: {
    JumpAtcontent() {
      const url = "../atcontent/main";
      if (mpvuePlatform === "wx") {
        mpvue.switchTab({ url });
      } else {
        mpvue.navigateTo({ url });
      }
      // mpvue.navigateTo({ url: "../atcontent/main" });
    },
    JumPindex() {
      mpvue.navigateTo({ url: "../index/main" });
    }
  },

  created() {},
  mounted() {}
};
</script>

<style>
.logsIndexHeader img {
  width: 828rpx;
}
.logsIndexContent p {
  margin: 20rpx;
}
.logsIndexContent li {
  border-top: 1px solid rgb(240, 240, 240);
  border-bottom: 1px solid rgb(240, 240, 240);
  padding: 20rpx;
  display: flex;
  align-items: center;
}
.span1 {
  flex: 2;
  color: darksalmon;
}
.span2 {
  flex: 4;
  overflow: hidden; /*自动隐藏文字*/
  text-overflow: ellipsis; /*文字隐藏后添加省略号*/
  white-space: nowrap; /*强制不换行*/
  width: 20em; /*不允许出现半汉字截断*/
}
.span3 {
  flex: 3;
  color: #777777;
}
.span4 {
  flex: 1;
  color: brown;
}
.Jdsy {
  height: 80rpx;
  line-height: 80rpx;
  width: 80rpx;
  border-radius: 50%;
  background-color: powderblue;
  text-align: center;
  font-size: 12px;
  color: white;
  position: fixed;
  bottom: 50px;
  right: 5px;
}
.logsIndexContent img {
  width: 70rpx;
  height: 70rpx;

  border-radius: 50%;
}
</style>
