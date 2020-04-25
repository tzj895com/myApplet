<template>
  <div class="box">
    <vlhead></vlhead>
    <p>当前第8题/共8题</p>
    <span>8.你的学历是?(单选)</span>
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
    <div class="volume1but" @click="JumpVl9">下一题</div>
  </div>
</template>

<script>
import vlhead from "../../../components/volhead";
export default {
  props: {},
  data() {
    return {
      items: [
        { id: "A", value: "初中" },
        { id: "B", value: "中专", checked: "true" },
        { id: "C", value: "高中" },
        { id: "D", value: "大专" },
        { id: "E", value: "本科" },
        { id: "F", value: "硕士" },
        { id: "G", value: "博士" },

      ]
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

