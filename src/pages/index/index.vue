<template>
  <div>
    <div v-if="flag" class="box">
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
    <!-- 授权 -->
    <div v-else>
      <div class="headView">
        <div class="headImageView">
          <open-data type="userAvatarUrl" class="img"></open-data>
        </div>
        <div class="titleText">申请获取以下权限</div>
        <div class="contentText">获得你的公开信息(昵称,头像,手机等)</div>
        <button
          class="authBtn"
          type="primary"
          open-type="getUserInfo"
          @getuserinfo="bindGetUserInfo"
        >授权登录</button>
      </div>
    </div>

    <!-- /授权 -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      imgUrls: [
        "https://image.zymcloud.com/image/head/20190816/4e9febad26224fd595d451c12fc0ad9d.jpeg",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/coursePicture/0fbcfdf7-0040-4692-8f84-78bb21f3395d",
        "http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/management-school-picture/7683b32e-4e44-4b2f-9c03-c21f34320870"
      ],
      code: "",
      flag: false
    };
  },

  components: {},
  mounted() {},

  methods: {
    JumpActivity() {
      mpvue.navigateTo({ url: "../activity/main" });
    },
    JumpVolume1() {
      mpvue.navigateTo({ url: "../volume/volume1/main" });
    },
    bindGetUserInfo: function(e) {
      var mythis = this;
      wx.getSetting({
        success(res) {
          if (res.authSetting["scope.userInfo"]) {
            console.log("已经授权，可以直接调用");
            wx.getUserInfo({
              success: function(res) {
                console.log(res.userInfo);
                if (res.userInfo) {
                  wx.login({
                    success(res) {
                      if (res.code) {
                        mythis.$http
                          .post(
                            "https://mp.zymcloud.com/hp-hd/applet/activity/getAppid",
                            {
                              code: res.code
                            }
                          )
                          .then(res => {
                            console.log("后台交互返回值:", res);
                            mythis.flag = true;
                          });
                      } else {
                        console.log("登录失败！" + res.errMsg);
                      }
                    }
                  });
                }
              }
            });
          } else {
            console.log("用户点击了取消");
          }
        }
      });
    }
  },

  created() {
    var that = this;
    wx.getSetting({
      success: function(res) {
        if (res.authSetting["scope.userInfo"]) {
          console.log("用户授权了");
          that.flag = true;
        } else {
          //用户没有授权
          console.log("用户没有授权");
          that.flag = false;
        }
      }
    });
  }
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

.headView {
  margin: 90rpx 50rpx 90rpx 50rpx; /*上右下左*/
}
.headImageView {
  display: block;
  margin-left: 25px;
  margin-top: 25px;
  margin-right: 25px;
  margin-bottom: 0px;
}
.headImageView .headImage {
  width: 50%;
  /* height: 80%; */
}

.titleText {
  margin-left: 25px;
  margin-top: 25px;
  margin-bottom: 10px;
  font-size: 14px;
  color: #020e0f;
  text-align: center;
}

.contentText {
  margin-left: 25px;
  margin-top: 0px;
  margin-bottom: 0px;
  font-size: 14px;
  color: #666;
  text-align: center;
}

.authBtn {
  margin-top: 35px;
  margin-left: 25px;
  margin-right: 25px;
  height: 45px;
  font-size: 17.5px;
}
.headImageView .img {
  display: block;
  width: 50%;
  margin: 0 auto;
}
</style>
