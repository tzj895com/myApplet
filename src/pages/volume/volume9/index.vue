<template>
  <div class="box">
    <vlhead></vlhead>
    <p>* 请留下你的联系方式,您提交完问卷后可参与抽奖,中奖后工作人员会第一时间联系您!</p>
    <div class="box_input">
      <span>姓名:</span>
      <input type="text" name id />
    </div>
    <div class="box_input">
      <span>电话:</span>
      <input type="text" name id />
    </div>
    <div class="box_radio">
      <span>性别:</span>
      <view class="page__bd">
        <view class="section section_gap">
          <radio-group class="radio-group">
            <radio class="radio" v-for="(item,index) in items" :key="index">
              <text class="radio2">{{item.value}}</text>
            </radio>
          </radio-group>
        </view>
      </view>
    </div>
    <div class="box_picker">
      <span>出生日期:</span>
      <view class="section">
        <picker mode="date" :value="date" start="1600-09-01" end="2020-09-01">
          <view class="picker">
            <span>{{date}}</span>
            <span>></span>
          </view>
        </picker>
      </view>
    </div>

    <!-- 抽奖 -->
    <div class="rotary-table">
      <div
        :class="current==index?'award1':'award'"
        v-for="(award,index) in awards"
        :key="index"
      >{{award.name}}</div>
    </div>
    <div id="start-btn" @click="start">开始</div>
    <!-- 抽奖 -->

    <div class="volume1but" @click="JumpVl9">提交</div>
  </div>
</template>

<script>
import vlhead from "../../../components/volhead";
export default {
  props: {},
  data() {
    return {
      items: [
        { id: "A", value: "男" },
        { id: "B", value: "女", checked: "true" }
      ],
      date: "2016-09-01",
      // 抽奖部分-------
      current: 0,
      awards: [
        { id: 1, name: "空" },
        { id: 2, name: "眼镜" },
        { id: 3, name: "包" },
        { id: 4, name: "笨驴" },
        { id: 5, name: "书" },
        { id: 6, name: "手链" },
        { id: 7, name: "美女" },
        { id: 8, name: "iphone" }
      ],
      speed: 200,
      diff: 15,
      award: {},
      time: 0
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    JumpVl9() {
      mpvue.navigateTo({ url: "../volume9/main" });
    },
    start() {
      var mythis = this;
      var num = 0;
      clearInterval(iab);
      let iab = setInterval(function() {
        num++;
        if (num == 10) {
          clearInterval(i);
          return;
        }
        mythis.current = Math.floor(Math.random() * 8);
        console.log(mythis.current);
      }, 1000);
    }
  },
  components: {
    vlhead
  }
};
</script>


<style>
.box p {
  margin: 20rpx 0rpx 20rpx 40rpx;
}

.volume1but {
  text-align: center;
  width: 400rpx;
  margin: 50rpx auto;
  padding: 20rpx;
  background-color: rgb(81, 169, 51);
  color: white;
  border-radius: 15rpx;
}
.box_input {
  margin: 50rpx 0;
  display: flex;
  align-items: center;
}
.box_input span {
  flex: 2;
}
.box_input input {
  flex: 8;
  border-radius: 10rpx;
  margin: 0rpx 100rpx 0 10rpx;
  border: 1rpx solid #7777;
  padding: 10rpx 20rpx;
}
.box_radio {
  display: flex;
  margin: 50rpx 0;
}
.box_radio span {
  flex: 2;
}
.box_radio .page__bd {
  flex: 8;
}
.radio {
  margin-right: 20rpx;
}
.box_picker {
  margin: 50rpx 0;
}
.box_picker .section {
  margin-left: 20rpx;
  border: 1rpx solid #7777;
  width: 300rpx;
  padding: 10rpx 20rpx;
}
.box_picker .section .picker {
  display: flex;
  justify-content: space-between;
}

.box_picker {
  display: flex;
  align-items: center;
}
.award {
  width: 33.3%;
  width: 200rpx;
  height: 200rpx;
  background-color: salmon;
}
.award1 {
  width: 33.3%;
  width: 200rpx;
  height: 200rpx;
  background-color: wheat;
}
.rotary-table {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}
</style>

