<template>
  <div>
    <div class="babbar_bottom">
      <ul>
        <li class="babbar_bottom_li" @click="indexbut">
          <img :src="srcimg" alt />
          <span :class="flag?'fonziyan':''">首页</span>
        </li>
        <li class="babbar_bottom_li" @click="indexbut1">
          <img :src="srcimg1" alt />
          <span :class="flag1?'fonziyan':''">排行</span>
        </li>
        <li class="babbar_bottom_li">
          <img src="/static/tabs/home.png" alt />
          <span class>说明</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      srcimg: "/static/tabs/home-active.png",
      srcimg1: "/static/tabs/orders.png",
      flag: true,
      flag1: false
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {
    srcimg(e) {
      this.flag = false;
    }
  },
  methods: {
    indexbut() {
      this.srcimg = "/static/tabs/home-active.png";
      this.srcimg1 = "/static/tabs/orders.png";
      this.flag = true;
      this.flag1 = !this.flag;
      mpvue.navigateTo({ url: "../atcontent/main" });
    },
    indexbut1() {
      this.srcimg = "/static/tabs/home.png";
      this.srcimg1 = "/static/tabs/orders-active.png";
      this.flag1 = true;
      this.flag = !this.flag1;
      mpvue.navigateTo({ url: "../paiha/main" });
    },
    changTab(index) {
      this.tab = index;
    }
  },
  components: {}
};
</script>

<style>
.babbar_bottom ul {
  width: 100%;
  display: flex;
  text-align: center;
  justify-content: center;
  position: fixed;
  bottom: 0px;
}
.babbar_bottom li {
  height: 100rpx;
  width: 33.33%;
  padding: 0 0 20rpx 0;
  background-color: white;
  color: #777777;
  font-size: 20rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.babbar_bottom_li img {
  width: 30%;
  height: 60rpx;
  margin: 15rpx;
}
.fonziyan {
  color: rgb(255, 209, 97);
}
.tab-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 48px;
  background: white;
  display: flex;
  padding-bottom: env(safe-area-inset-bottom);
}

.tab-bar-border {
  background-color: rgba(0, 0, 0, 0.33);
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 1px;
  transform: scaleY(0.5);
}

.tab-bar-item {
  flex: 1;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.tab-bar-item cover-image {
  width: 27px;
  height: 27px;
}

.tab-bar-item cover-view {
  font-size: 10px;
}
</style>
