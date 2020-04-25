<template>
  <div class="box">
    <div class="box1">
      <!-- 选手信息模块 -->
      <div class="boximag">
        <img class="userinfo-avatar" src="/static/images/user.png" background-size="cover" />
        <p>洪晟</p>
      </div>
      <!-- /选手信息模块 -->

      <!-- 排名投票信息模块 -->
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
      <!-- /排名投票信息模块 -->

      <!-- 选手描述 -->
      <div class="Middle_onde">
        <p>选手描述</p>
        <div>这家伙很懒什么都没有留下 ~</div>
      </div>
      <!-- /选手描述 -->
      <div class="Middle_onde">
        <p>选手照片</p>
        <img class="Middle_ondeimg"
          src="https://bkimg.cdn.bcebos.com/pic/3c6d55fbb2fb4316dbe830c722a4462308f7d39c?x-bce-process=image/watermark,g_7,image_d2F0ZXIvYmFpa2U5Mg==,xp_5,yp_5"
          alt
        />
      </div>
      <!-- /选手描述 -->

      <!-- 票数贡献榜 -->
      <div class="Middle_two">
        <h1>票数贡献榜</h1>
        <!-- 这里加滚动条 -->
        <view class="page-section-spacing">
          <scroll-view scroll-y="true" style="height: 1000rpx;">
            <div class="toupiao_juan">
              <img class="userinfo-avatar1" src="/static/images/aixin.png" />
              <span @click="JumpGive">送ta礼物加卷</span>
            </div>
            <div class="Middle_onde">
              <p>投票记录</p>
              <ul>
                <li class="li">
                  <i>
                    <span>zhangsan</span>
                    <br />
                    <span>2022-11-10</span>
                    <span>15:48</span>
                  </i>
                  <i class="iyanse">+1</i>
                </li>
                <li class="li">
                  <i>
                    <span>zhangsan</span>
                    <br />
                    <span>2022-11-10</span>
                    <span>15:48</span>
                  </i>
                  <i class="iyanse">+1</i>
                </li>
                <li class="li">
                  <i>
                    <span>zhangsan</span>
                    <br />
                    <span>2022-11-10</span>
                    <span>15:48</span>
                  </i>
                  <i class="iyanse">+1</i>
                </li>
                <li class="li">
                  <i>
                    <span>zhangsan</span>
                    <br />
                    <span>2022-11-10</span>
                    <span>15:48</span>
                  </i>
                  <i class="iyanse">+1</i>
                </li>
                <li class="li">
                  <i>
                    <span>zhangsan</span>
                    <br />
                    <span>2022-11-10</span>
                    <span>15:48</span>
                  </i>
                  <i class="iyanse">+1</i>
                </li>
              </ul>
            </div>
            <div class="bottom_chakan">
              <span>查看更多</span>
            </div>
          </scroll-view>
        </view>
      </div>
      <!-- /票数贡献榜 -->
    </div>
    <!-- taber栏 -->
    <div class="babbar_bottom">
      <ul>
        <li @click="JumpAtcontent">首页</li>
        <li>投票</li>
        <li>送礼</li>
      </ul>
    </div>
    <!-- /taber栏 -->
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {};
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
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
    JumpGive() {
      mpvue.navigateTo({ url: "../give/main" });
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
  margin: 0 30rpx 0 30rpx;
}
.boximag .userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}
.box .userinfo-avatar1 {
  width: 400rpx;
  height: 300rpx;
  /* margin: 20rpx; */
}
.boximag {
  /* margin: 0 auto; */
  display: flex;
  flex-direction: column;
  align-items: center;
}
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

.Middle_onde p {
  text-align: center;
  padding: 20rpx;
  border-bottom: 1px solid rgb(245, 245, 245);
}
.Middle_onde div {
  padding: 50rpx 0 0rpx 50rpx;
  height: 100rpx;
  color: rgb(206, 206, 206);
}
.Middle_onde {
  background-color: white;
  margin-bottom: 20rpx;
}
.box .Middle_onde img {
  width: 620rpx;
  margin: 20rpx 0 40rpx 30rpx;
}
.Middle_two h1 {
  color: white;
  background-color: wheat;
  text-align: center;
  padding: 10rpx;
}
.toupiao_juan {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.toupiao_juan span {
  padding: 15rpx 100rpx;
  color: white;
  background-color: cornflowerblue;
  border-radius: 30rpx;
  margin-bottom: 100rpx;
}
.li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20rpx 0 10rpx 20rpx;
  border-bottom: 1px solid rgb(245, 245, 245);
}
.bottom_chakan {
  text-align: center;
  padding: 15rpx 100rpx;
  color: white;
  background-color: cornflowerblue;
  margin: 40rpx 20rpx 150rpx 20rpx;
}

.babbar_bottom ul {
  width: 100%;
  display: flex;
  text-align: center;
  justify-content: center;
  position: fixed;
  bottom: 0px;
}
.babbar_bottom li {
  width: 33.3%;
  padding: 30rpx;
  background-color: cornflowerblue;
  color: white;
}
.Middle_onde span {
  color: #777777;
}
.Middle_onde .iyanse {
  color: cornflowerblue;
}
</style>
