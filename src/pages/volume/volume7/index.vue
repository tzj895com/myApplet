<template>
  <div class="box">
    <vlhead></vlhead>
    <p>当前第7题/共8题</p>
    <span>7.你是否是应届生/非应届生?(单选)</span>
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
    <div class="volume1but" @click="JumpVl8">下一题</div>
  </div>
</template>

<script>
import vlhead from "../../../components/volhead";
export default {
  props: {},
  data() {
    return {
      items: [
        { id: "A", value: "应届" },
        { id: "B", value: "非应届", checked: "true" },

 
      ]
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    JumpVl8() {
      mpvue.navigateTo({ url: "../volume8/main" });
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

