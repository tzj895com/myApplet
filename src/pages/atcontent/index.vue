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
        <p>{{Signedup}}</p>
        <p>已报名</p>
      </div>
      <div>
        <p>{{Totalvotes}}</p>
        <p>总投票</p>
      </div>
      <div>
        <p>{{Views1}}</p>
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
      <input type="text" placeholder="姓名" v-model="search" />
      <span @click="search1">搜索</span>
    </div>
    <!-- /搜索查询 -->

    <!-- 分组查询 -->
    <div class="atcontent_Grouping">
      <picker mode="selector" :range="array" :value="index" @change="dateChange" class="weui-input">
        <div class="divspan">
          <span class="span1">{{array[index]}}</span>
          <span>></span>
        </div>
      </picker>
    </div>

    <!-- /分组查询 -->

    <!-- 选手信息模块 -->
    <div class="atcontent_Content" v-if="rowsfla">
      <div
        class="atcontent_Content_1"
        @click="JumpGrvote"
        v-for="(item,index) in rows"
        :key="index"
      >
        <img :src="item.coverImg" alt />
        <p class="p1">{{item.name}}</p>
        <p class="p2">{{item.ticket}}票</p>
        <p class="p3">选择投票</p>
      </div>
    </div>
    <div class="atcontent_Content" v-else>
      <div
        class="atcontent_Content_1"
        @click="JumpGrvote"
        v-for="(item,index) in myrows"
        :key="index"
      >
        <img :src="item.coverImg" alt />
        <p class="p1">{{item.name}}</p>
        <p class="p2">{{item.ticket}}票</p>
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
      imgUrls: [],
      day: "0",
      hour: "00",
      min: "00",
      second: "00",
      innerAudioContext: null, // 音频对象
      playImg: "../../static/img/play.png", // 播放或者暂停图片
      rotate: false,
      array: ["全部", "北大青鸟鲁广校区", "北大青鸟徐东校区", "分组一", "null"],
      index: 0,
      // 投票数据
      Signedup: "",
      Totalvotes: "",
      Views1: "",
      // --
      emd: "", //倒计时时间
      rows: [],
      myrows: [],
      rowsfla: true,
      search: "" //搜索的值
    };
  },
  computed: {},
  created() {
    this.gteindex();
    this.gtesearch();
  },
  mounted() {
    this.audioPlay();
    this.countTime();
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
      var endTime = this.emd;
      console.log(this.emd);

      var newTime = endTime.replace(/-/g, "/");
      var endDate = new Date(newTime);

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

      this.innerAudioContext.src = "http://mp3.dwjgrw.cn/down/31389.mp3";
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
    },
    // 首页数据
    gteindex() {
      this.$http
        .post("https://mp.zymcloud.com/hp-hd/applet/activity/list", {
          activityId: 1
        })
        .then(res => {
          // console.log(res.data);
          this.imgUrls.push(res.data.coverList[0].url);
          this.Signedup = res.data.hdActivity.enroll;
          this.Totalvotes = res.data.hdActivity.sumVote;
          this.Views1 = res.data.hdActivity.browse;
          this.emd = res.data.hdActivity.end;
        });
    },
    gtesearch() {
      this.$http
        .post(
          "https://mp.zymcloud.com/hp-hd/applet/activity/activityPlayer",
          {}
        )
        .then(res => {
          // console.log(res);
          this.rows = res.rows.slice(0, 58);
          // console.log(this.rows);
        });
    },
    dateChange(e) {
      if (e.mp.detail.value == 1) {
        this.myrows = this.rows.filter(
          item => item.groupName == "北大青鸟鲁广校区"
        );
        this.index = 1;
        this.rowsfla = false;
        return;
      }
      if (e.mp.detail.value == 2) {
        this.myrows = this.rows.filter(
          item => item.groupName == "北大青鸟鲁广校区"
        );
        this.index = 2;
        this.rowsfla = false;
        return;
      }
      if (e.mp.detail.value == 3) {
        this.myrows = this.rows.filter(item => item.groupName == "分组一");
        this.rowsfla = false;
        this.index = 3;
        return;
      }
      if (e.mp.detail.value == 4) {
        this.myrows = this.rows.filter(item => item.groupName == null);
        this.rowsfla = false;
        this.index = 4;
        return;
      } else {
        this.rowsfla = true;
        this.index = 0;
        return;
      }
    },
    search1() {
      console.log(1);

      this.myrows = this.rows.filter(item => item.name == this.search);
      this.rowsfla = false;
    }
  },
  onUnload() {
    this.innerAudioContext.stop();
  },
  components: {}
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
  font-size: 24rpx;
}
.atcontent_Grouping .span1 {
  margin-right: 20rpx;
  margin-left: 20rpx;
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
.box .muisbut {
  width: 70rpx;
  height: 70rpx;
  border-radius: 50%;
  position: fixed;
  top: 50rpx;
  right: 50rpx;
  border: 3rpx solid cornflowerblue;
}
</style>

