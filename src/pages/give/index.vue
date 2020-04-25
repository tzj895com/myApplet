<template>
  <div class="box">
    <div class="box1">
      <!-- 头部个人信息img -->
      <div class="boximag">
        <img class="userinfo-avatar" src="/static/images/user.png" background-size="cover" />
        <p>洪晟</p>
      </div>
      <!-- /头部个人信息img -->

      <!-- 个人投票礼物详情 -->
      <div class="atcontent_information">
        <div>
          <p>1</p>
          <p>排名</p>
        </div>
        <div>
          <p>999+</p>
          <p>票数</p>
        </div>
        <div>
          <p>999+</p>
          <p>礼物</p>
        </div>
        <div>
          <p>45699</p>
          <p>浏览量</p>
        </div>
      </div>
      <!-- /个人投票礼物详情 -->

      <!-- 礼物栏 -->
      <div class="give_Gift">
        <div class="give_Gift_column">送礼物加票数</div>
        <div class="give_Gift_content">
          <div class="give_Gift_content_1">
            <span>棒棒糖</span>
            <img
              src="https://dss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1185121673,2591088608&fm=26&gp=0.jpg"
              alt
            />
            <span class="give_Gift_content_span">+20</span>
          </div>
          <div class="give_Gift_content_1">
            <span>花花</span>
            <img src="http://img4.imgtn.bdimg.com/it/u=2647476514,1208495136&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+65</span>
          </div>
          <div class="give_Gift_content_1">
            <span>么么哒</span>
            <img src="http://img2.imgtn.bdimg.com/it/u=1660989034,3174872246&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+94</span>
          </div>
          <div class="give_Gift_content_1">
            <span>666</span>
            <img src="http://img3.imgtn.bdimg.com/it/u=3978817709,2012155076&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+240</span>
          </div>
          <div class="give_Gift_content_1">
            <span>告白气球</span>
            <img src="http://img3.imgtn.bdimg.com/it/u=1444852199,1728034402&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+550</span>
          </div>
          <div class="give_Gift_content_1">
            <span>小心心</span>
            <img src="http://img5.imgtn.bdimg.com/it/u=1259629594,416799451&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+1000</span>
          </div>
          <div class="give_Gift_content_1">
            <span>神灯</span>
            <img src="http://img2.imgtn.bdimg.com/it/u=809861163,3405593303&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+2188</span>
          </div>
          <div class="give_Gift_content_1">
            <span>皇冠</span>
            <img src="http://img3.imgtn.bdimg.com/it/u=1496762410,3930670587&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+2888</span>
          </div>
          <div class="give_Gift_content_1">
            <span>宝箱</span>
            <img src="http://img5.imgtn.bdimg.com/it/u=3968376577,3875156126&fm=26&gp=0.jpg" alt />
            <span class="give_Gift_content_span">+6888</span>
          </div>
        </div>
        <!-- 计算 -->
        <div class="give_Gift_Calculation">
          <div class="give_Gift_Calculation1">
            <span>${{Price *num}}</span>
            <span class="give_Gift_Calculation1_span">+{{Votes *num}}票</span>
          </div>
          <div class="give_Gift_Calculation2">
            <button @click="butReduce">-</button>
            <span>{{num}}</span>
            <button @click="butPlus">+</button>
          </div>
        </div>
        <!-- /计算 -->
      </div>
      <!-- /礼物栏 -->
    </div>
    <!-- 送出button -->
    <div class="bottonbut">立即送出</div>
    <!-- /送出button -->
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      Price: 6,
      Votes: 20,
      num: 10
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    butReduce() {
      if (this.num <= 1) {
        wx.showToast({
          title: "不能再删了",
          icon: "success",
          duration: 2000
        });
        return;
      } else {
        this.num--;
      }
    },
    butPlus() {
      if (this.num < 99) {
        this.num++;
      } else {
        wx.showToast({
          title: "不能再删了",
          icon: "success",
          duration: 2000
        });

        return;
      }
    }
  },
  components: {}
};
</script>

<style>
.box {
  background-color: rgb(245, 245, 245);
}
.box1 {
  margin: 0 30rpx 120rpx 30rpx;
}
/* 头部个人信息img */
.boximag .userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}
.boximag {
  display: flex;
  flex-direction: column;
  align-items: center;
}
/* /头部个人信息img */

/* 个人投票礼物详情 */
.atcontent_information {
  display: flex;
  text-align: center;
  background-color: cornflowerblue;
  margin: 20rpx 0;

  padding: 20rpx;
}
.atcontent_information div {
  flex: 1;
  color: white;
}
/* /个人投票礼物详情 */

/* 礼物栏 */
.give_Gift {
  background-color: rgb(238, 238, 238);
}
.give_Gift_column {
  background-color: white;
  color: #777777;
  padding: 20rpx;
  font-size: 24rpx;
}
.give_Gift_content {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  /* box-sizing: border-box; */
  /* padding: 20rpx; */
  font-size: 24rpx;
}
.give_Gift_content_1 {
  background-color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #777777;
  width: 31%;
  margin: 2% 1% 0 1%;
}
.give_Gift_content img {
  width: 128rpx;
  height: 100rpx;
  margin: 20rpx 0;
}
.give_Gift_content_span {
  background-color: yellowgreen;
  width: 100%;
  text-align: center;
  border-bottom: 3px solid rgba(33, 54, 13, 0.658);
}
/* 计算 */
.give_Gift_Calculation {
  padding: 10rpx;
  margin-top: 40rpx;
  display: flex;
  justify-content: space-between;
  color: #777777;
}
.give_Gift_Calculation2 button {
  height: 50rpx;
  width: 50rpx;
  line-height: 50rpx;
  text-align: center;
}
.give_Gift_Calculation2 span {
  width: 80rpx;
  height: 50rpx;
  text-align: center;
  line-height: 50rpx;
}
.give_Gift_Calculation2 {
  display: flex;
}
.give_Gift_Calculation1_span {
  margin-left: 20rpx;
  font-size: 22rpx;
}
/* /礼物栏 */

/* button按钮 */
.bottonbut {
  height: 80rpx;
  line-height: 80rpx;
  width: 100%;
  background-color: cornflowerblue;
  text-align: center;
  position: fixed;
  bottom: 0rpx;
}
/* /button按钮 */
</style>
