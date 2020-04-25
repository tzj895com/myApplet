<template>
  <div class="box">
    <vlhead></vlhead>
    <p>* 请留下你的联系方式,您提交完问卷后可参与抽奖,中奖后工作人员会第一时间联系您!</p>


    <div class="volume1but" @click="JumpVl9">提交</div>
  </div>
</template>

<script>
import vlhead from "../../../components/volhead";
export default {
  props: {},
  data() {
    return {

    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    JumpVl9() {
      mpvue.navigateTo({ url: "../volume9/main" });
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
</style>

