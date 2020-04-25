<template>
  <div class="box">
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

    <!-- 报名投票数据框 -->
    <div class="atcontent_information">
      <div>
        <p>60</p>
        <p>已报名</p>
      </div>
      <div>
        <p>999</p>
        <p>总投票</p>
      </div>
      <div>
        <p>45699</p>
        <p>浏览量</p>
      </div>
    </div>
    <!-- 报名投票数据框 -->

    <!-- 我要报名but -->
    <div class="atcontent_newspaper" @click="JumpEnterfor">我要报名</div>
    <!-- 我要报名but -->

    <!-- 活动倒计时 -->
    <div class="atcontent_Time">
      距离光棍节:
      <span>{{day}}天</span>
      <span>{{hour}}时</span>
      <span>{{min}}分</span>
      <span>{{second}}秒</span>
    </div>
    <!-- 活动倒计时 -->

    <!-- 搜索查询 -->
    <div class="atcontent_search">
      <input type="text" placeholder="姓名" />
      <span>搜索</span>
    </div>
    <!-- /搜索查询 -->

    <!-- 分组查询 -->
    <div class="atcontent_Grouping">
      <picker mode="selector" :range="array" :value="index" @change="dateChange" class="weui-input">
        <div class="divspan">
          <span class="span1">选择分组</span>
          <span>></span>
        </div>
      </picker>
    </div>
    <!-- /分组查询 -->

    <!-- 选手信息模块 -->
    <div class="atcontent_Content">
      <div class="atcontent_Content_1" @click="JumpGrvote">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/da11db5345/home_1.jpg"
          alt
        />
        <p class="p1">洪晟</p>
        <p class="p2">3票</p>
        <p class="p3">选择投票</p>
      </div>
      <div class="atcontent_Content_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/8156769438/home_2.jpg"
          alt
        />
        <p class="p1">洪晟</p>
        <p class="p2">3票</p>
        <p class="p3">选择投票</p>
      </div>
      <div class="atcontent_Content_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/1024x756/filters:focal(610x450:611x451):quality(100)/f/11/1220x900/cdab32ecc2/home_3.jpg"
          alt
        />
        <p class="p1">洪晟</p>
        <p class="p2">3票</p>
        <p class="p3">选择投票</p>
      </div>
      <div class="atcontent_Content_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/a8a87f5dcf/home_4.jpg"
          alt
        />
        <p class="p1">洪晟</p>
        <p class="p2">3票</p>
        <p class="p3">选择投票</p>
      </div>
      <div class="atcontent_Content_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/a8a87f5dcf/home_4.jpg"
          alt
        />
        <p class="p1">洪晟</p>
        <p class="p2">3票</p>
        <p class="p3">选择投票</p>
      </div>
      <div class="atcontent_Content_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/a8a87f5dcf/home_4.jpg"
          alt
        />
        <p class="p1">洪晟</p>
        <p class="p2">3票</p>
        <p class="p3">选择投票</p>
      </div>
      <div class="atcontent_Content_1">
        <img
          src="https://storyblok-image.ef.com.cn/unsafe/600x443/filters:focal(300x222:301x223):quality(100)/f/11/600x443/a8a87f5dcf/home_4.jpg"
          alt
        />
        <p class="p1">洪晟</p>
        <p class="p2">3票</p>
        <p class="p3">选择投票</p>
      </div>
    </div>
    <!-- /选手信息模块 -->



    <!-- 音乐播放器 -->
    <!-- <audio :poster="poster" :src="src" id="myAudio" controls:turs loop></audio> -->
    <img
      class="Rotation muisbut"
      @click="hanlerPaly"
      src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=114305995,3642623632&fm=26&gp=0.jpg"
      alt
    />
    <!-- /音乐播放器 -->
  </div>
</template>

<script>

export default {
  props: {},
  data() {
    return {
      imgUrls: [
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/newsPicture/05558951-de60-49fb-b674-dd906c8897a6",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/coursePicture/0fbcfdf7-0040-4692-8f84-78bb21f3395d",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/management-school-picture/7683b32e-4e44-4b2f-9c03-c21f34320870"
      ],
      day: "0",
      hour: "00",
      min: "00",
      second: "00",
      innerAudioContext: null, // 音频对象
      playImg: "../../static/img/play.png", // 播放或者暂停图片
      rotate: false,
      array: ["全部", "美国", "中国", "巴西", "日本"]
    };
  },
  computed: {},
  created() {
    this.countTime();
  },
  mounted() {
    this.audioPlay();
  },
  watch: {},
  methods: {
    JumpEnterfor() {
      mpvue.navigateTo({ url: "../enterfor/main" });
      this.innerAudioContext.stop();
    },
    JumpGrvote() {
      mpvue.navigateTo({ url: "../grvote/main" });
      this.innerAudioContext.stop();
    },
    // 倒计时
    countTime() {
      var endDate = new Date("2020-11-11:00:00:00");
      var thiss = this;
      setInterval(function() {
        var startDate = new Date();
        var totalSecond = (endDate - startDate) / 1000; //计算时间差
        var Sday = parseInt(totalSecond / 60 / 60 / 24);
        var Shouer = parseInt((totalSecond / 60 / 60) % 24);
        var Sminute = parseInt((totalSecond / 60) % 60);
        var Ssecond = parseInt(totalSecond % 60);

        thiss.day = Sday;
        thiss.hour = Shouer;
        thiss.min = Sminute;
        thiss.second = Ssecond;
      }, 1000);
    },
    audioPlay() {
      this.innerAudioContext = wx.createInnerAudioContext();

      this.innerAudioContext.src = "http://m10.music.126.net/20200424182921/f3f776aedc2a71c4464598253dbcba26/ymusic/341e/9cc2/7c4f/b13ac6e62d3625524dde95fd1b1628bf.mp3";
      this.innerAudioContext.autoplay = true;
    },

    hanlerPaly() {
      if (this.innerAudioContext.paused) {
        console.log("播放");

        this.innerAudioContext.play();
      } else {
        console.log("暂停");
        this.innerAudioContext.pause();
      }
    }
  },
  onUnload() {
    this.innerAudioContext.stop();
  },
  components: {

  }
};
</script>

<style>
.box {
  background-color: rgb(245, 245, 245);
}
.logsIndexHeader img {
  width: 828rpx;
}
.atcontent_information {
  display: flex;
  text-align: center;
  background-color: cornflowerblue;
  margin: 30rpx;
  padding: 20rpx;
}
.atcontent_information div {
  flex: 1;
  color: white;
}
.atcontent_newspaper {
  width: 370rpx;
  background-color: cornflowerblue;
  color: white;
  margin: 0 auto;
  text-align: center;
  padding: 20rpx;
  border-radius: 15rpx;
}
.atcontent_Time {
  margin: 30rpx;
  padding: 20rpx;
  text-align: center;
  color: white;
  background-color: cornflowerblue;
  border-radius: 15rpx;
}
.atcontent_Time span {
  margin-right: 10rpx;
  color: lightpink;
}
.atcontent_search {
  margin: 30rpx;
  padding: 20rpx;
  display: flex;
}
.atcontent_search input {
  flex: 7;
  border: 1px solid cornflowerblue;
  padding: 15rpx;
}
.atcontent_search span {
  flex: 3;
  background-color: cornflowerblue;
  border: 1px solid cornflowerblue;
  padding: 15rpx;
  color: white;
  text-align: center;
}
.atcontent_Grouping {
  width: 300rpx;
  margin: 30rpx;
  padding: 15rpx;
  background-color: cornflowerblue;
  color: white;
}
.atcontent_Grouping .span1 {
  margin-right: 80rpx;
  margin-left: 50rpx;
}
.atcontent_Content {
  display: flex;
  flex-wrap: wrap;
  /* justify-content: space-around; */
  margin-top: 20rpx;
}
.atcontent_Content_1 {
  display: flex;
  flex-direction: column;
  /* align-items: center; */
  background-color: white;
  margin-left: 25rpx;
  margin-bottom: 20rpx;
  padding: 20rpx;
}
.atcontent_Content_1 img {
  height: 300rpx;
  width: 300rpx;
}
.p1 {
  color: #777;
}
.p2 {
  color: cornflowerblue;
}

.p3 {
  padding: 15rpx;
  text-align: center;
  background-color: cornflowerblue;
  color: white;
}
.atcontent_Content p {
  margin: 5rpx 0;
}

.muisbut {
  width: 70rpx;
  height: 70rpx;
  border-radius: 50%;
  position: fixed;
  top: 50rpx;
  right: 50rpx;
  border: 3rpx solid cornflowerblue;
}
@-webkit-keyframes rotation {
  from {
    -webkit-transform: rotate(0deg);
  }
  to {
    -webkit-transform: rotate(360deg);
  }
}
.Rotation {
  -webkit-transform: rotate(360deg);
  animation: rotation 3s linear infinite;
  -moz-animation: rotation 3s linear infinite;
  -webkit-animation: rotation 3s linear infinite;
  -o-animation: rotation 3s linear infinite;
}
</style>

