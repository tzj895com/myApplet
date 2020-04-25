<template>
  <div class="box">
    <!-- 标题 -->
    <div class="entHeader">
      <p>在线报名</p>
    </div>
    <!-- /标题 -->

    <!-- input填写 -->
    <view class="weui-cell weui-cell_input">
      <div class="weui-inputdiv">
        <span>选手名称</span>
        <input class="weui-input" auto-focus placeholder=" 请输入选手姓名" v-model="name" />
      </div>
      <div class="weui-inputdiv">
        <span>手机号</span>
        <input class="weui-input" maxlength="11" placeholder=" 请输入手机号" v-model="regular" />
      </div>
      <div class="weui-inputdiv">
        <span>分组</span>

        <picker
          mode="selector"
          :range="array"
          :value="index"
          @change="dateChange"
          class="weui-input"
        >
          <div class="divspan">
            <p>{{array[index]}}</p>
            <p>>></p>
          </div>
        </picker>
      </div>
      <div class="weui-inputdiv1">
        <span>选手描述</span>
        <textarea cols="15" rows="5" class="weui-input1" placeholder="请输入描述内容"></textarea>
      </div>
    </view>
    <!-- /input填写 -->

    <!-- 照片上传模块 -->
    <p>上传选手照片(1~3张)</p>
    <div class="butimg">
      <span v-for="(item,index) in tempFilePaths1" :key="index">
        <img :src="tempFilePaths1[index]" alt />
      </span>

      <img v-if="flag" src="/static/images/but.png" alt @click="butimg" />
    </div>
    <!-- /照片上传模块 -->

    <!-- bottombut提交按钮 -->
    <div class="bottombut" @click="Submission">提交</div>
    <!-- bottombut提交按钮 -->
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      date: "",
      array: ["全部", "美国", "中国", "巴西", "日本"],
      index: 0,
      tempFilePaths1: [],
      flag: true,

      name: "",
      regular: ""
    };
  },

  computed: {},
  created() {},
  mounted() {},
  watch: {
    tempFilePaths1(e) {
      console.log(this.tempFilePaths1.length);
      if (this.tempFilePaths1.length === 3) {
        this.flag = !this.flag;
      }
    },
    name(e) {
      var reg = /^[\u4E00-\u9FA5\uf900-\ufa2d·s]{2,20}$/;
      if (this.name.length > 2) {
        if (!reg.test(e)) {
          wx.showToast({
            title: "姓名有误,请重填",
            icon: "none",
            duration: 1000
          });
        }
      }
    },
    regular(e) {
      var reg = /^1([38]\d|5[0-35-9]|7[3678])\d{8}$/;
      if (this.regular.length > 10) {
        console.log(reg.test(e));

        if (!reg.test(e)) {
          wx.showToast({
            title: "手机号码有误，请重填",
            icon: "none",
            duration: 1000
          });
        }
      }
    }
  },
  methods: {
    dateChange: function(e) {
      console.log("picker发送选择改变，携带值为", e.mp.detail.value);
      //注意：不是官网的e.detail.value,而是 e.mp.detail.value
      this.index = e.mp.detail.value;
    },
    butimg() {
      var mythis = this;
      wx.chooseImage({
        count: 1, //选择图片个数1-9
        sizeType: ["original", "compressed"], //original原图,compressed压缩图
        sourceType: ["album", "camera"], //album从相册选图,camera使用相机
        success(res) {
          // tempFilePath可以作为img标签的src属性显示图片
          var tempFilePaths = res.tempFilePaths;
          // console.log(tempFilePaths);
          mythis.tempFilePaths1.push(...tempFilePaths);
          // console.log(mythis.tempFilePaths1);
        }
      });
    },
    Submission() {
      if (this.name < 1) {
        wx.showToast({
          title: "请填写姓名",
          icon: "none",
          duration: 1000
        });
        return;
      }
      if (this.regular < 1) {
        wx.showToast({
          title: "请填写手机号",
          icon: "none",
          duration: 1000
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
  margin: 40rpx;
  /* background-color: rgb(245, 245, 245); */
}
.entHeader {
  text-align: center;
  height: 100rpx;
  border-bottom: 1rpx solid rgb(125, 138, 126);
  font-size: 40rpx;
  /* 125138126 */
  color: rgb(125, 138, 126);
}
.weui-cell {
  margin-top: 50rpx;
}
.weui-input {
  border: 1px solid rgb(245, 245, 245);
  height: 80rpx;
  width: 400rpx;
  line-height: 80rpx;
  background-color: rgb(250, 251, 253);
  margin: 0 40rpx;
  flex: 5;
}
.weui-input1 {
  border: 1px solid rgb(245, 245, 245);
  /* height: 400rpx;
  width: 200rpx; */
  /* line-height: 80rpx; */
  background-color: rgb(250, 251, 253);
  margin: 0 40rpx;
  flex: 5;
  padding-top: 15rpx 0 0 15rpx;
}
.weui-inputdiv {
  display: flex;
  align-items: center;
  margin-top: 15rpx;
}
.weui-inputdiv1 {
  display: flex;
  /* align-items: center; */
  margin-top: 15rpx;
}
.weui-inputdiv1 span {
  color: steelblue;
  font-size: 35rpx;
  flex: 2;
}
.weui-inputdiv span {
  color: steelblue;
  font-size: 35rpx;
  flex: 2;
}
.aaaaaaa {
  background-color: tan;
  height: 200rpx;
}
.divspan {
  display: flex;
  justify-content: space-between;
  color: rgb(125, 138, 126);
  padding-left: 10rpx;
}
.bottombut {
  /* padding: 100rpx; */

  width: 650rpx;
  height: 80rpx;
  line-height: 80rpx;
  border-radius: 15rpx;
  background-color: #6495ed;
  text-align: center;
  position: fixed;
  left: 50rpx;
  bottom: 50rpx;
  color: white;
}
.butimg img {
  width: 200rpx;
  height: 180rpx;
}
</style>
