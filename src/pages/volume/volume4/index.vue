<template>
  <div class="box">
    <vlhead></vlhead>
    <p>当前第3题/共8题</p>
    <span>3.你通过哪种渠道找到我们学校的?(单选)</span>
    <view class="page__bd">
      <view class="section section_gap">
        <radio-group class="radio-group">
          <ul>
            <li v-for="(item,index) in items" :key="index">
              <radio class="radio">
                <text>{{item.id}}.</text>
                <text>{{item.value}}</text>
              </radio>
            </li>
          </ul>
        </radio-group>
      </view>
    </view>
    <div class="volume1but" @click="JumpVl5">下一题</div>
  </div>
</template>

<script>
import vlhead from "../../../components/volhead";
export default {
  props: {},
  data() {
    return {
      items: [
        { id: "A", value: "在读生推荐" },
        { id: "B", value: "毕业生推荐", checked: "true" },
        { id: "C", value: "老师介绍" },
        { id: "D", value: "百度" },
        { id: "E", value: "360" },
        { id: "F", value: "抖音" },
        { id: "G", value: "头条" },
        { id: "H", value: "其他网络搜索" },
        { id: "I", value: "地铁广告" },
        { id: "J", value: "校园宣讲" },
        { id: "K", value: "地铁广告" },
        { id: "L", value: "户外页单" },
        { id: "M", value: "其他" },
      ]
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    JumpVl5() {
      mpvue.navigateTo({ url: "../volume5/main" });
    }
  },
  components: {
    vlhead
  }
};
</script>


<style>
.box span {
  font-weight: 700;
  margin-left: 20rpx;
}
.box p {
  margin: 20rpx 0rpx 20rpx 40rpx;
}
.radio-group ul {
  border: 1rpx solid #7777;
  margin: 20rpx;
}

.radio-group li {
  padding: 20rpx 0 20rpx 20rpx;
  border-top: 1rpx solid #7777;
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
