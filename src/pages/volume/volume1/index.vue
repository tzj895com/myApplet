<template>
  <div class="box">
    <vlhead></vlhead>
    <div class="volume1">
      <p>您好!</p>
      <span>感谢您对武汉宏鹏教育的支持与信任,我们教育改变生活的理念,在我校全体教职员工的努力下,已经帮助数万学生,实现了自己的人生理想和学习目标.您的宝贵意见将指导我们在今后的工作中不断努力改进,请务必认真填写!</span>
    </div>
    <div class="volume1but" @click="JumpVl2">开始调查问卷</div>
  </div>
</template>

<script>
import vlhead from "../../../components/volhead";
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
    JumpVl2() {
      mpvue.navigateTo({ url: "../volume2/main" });
    }
  },
  components: {
    vlhead
  }
};
</script>


<style>
.volume1 {
  margin: 50rpx;
  padding: 50rpx;
  box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.5);
}
.volume1 span {
  margin-left: 50rpx;
}
.volume1but {
  text-align: center;
  width: 400rpx;
  margin: 0 auto;
  padding: 20rpx;
  background-color: rgb(81, 169, 51);
  color: white;
  border-radius: 15rpx;
}
</style>
