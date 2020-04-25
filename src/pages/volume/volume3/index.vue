<template>
  <div class="box">
    <vlhead></vlhead>
    <p>当前第2题/共8题</p>
    <span>2.你选择学校最看重哪些?(多选)</span>
    <checkbox-group>
      <ul>
        <li v-for="(item,index) in items" :key="index">
          <label class="checkbox">
            <checkbox :value="item.id" />
            <text>{{item.id}}.</text>
            <text>{{item.value}}</text>
          </label>
        </li>
      </ul>
    </checkbox-group>
    <div class="volume1but" @click="JumpVl4">下一题</div>
  </div>
</template>

<script>
import vlhead from "../../../components/volhead";
export default {
  props: {},
  data() {
    return {
      items: [
        { id: "A", value: "教学质量" },
        { id: "B", value: "就业保障", checked: "true" },
        { id: "C", value: "品牌知名度" },
        { id: "D", value: "课程设置" },
        { id: "E", value: "口碑美誉度" },
        { id: "F", value: "办学规模" },
        { id: "G", value: "校园环境" },
        { id: "H", value: "住宿条件" },
        { id: "L", value: "性价比" },
        { id: "Q", value: "其他" }
      ]
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    JumpVl4() {
      mpvue.navigateTo({ url: "../volume4/main" });
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
checkbox-group ul {
  border: 1rpx solid #7777;
  margin: 20rpx;
}

checkbox-group li {
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
