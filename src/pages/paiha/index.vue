<template>
  <div class="box">
    <div class="box1">
      <!-- 排行倒计时 -->
      <div class="paiha_time">
        <p class="paiha_time_p">2020-11-11 00:00:00 结束</p>
        <p>
          <span>{{day}}天</span>
          <span>{{hour}}时</span>
          <span>{{min}}分</span>
          <span>{{second}}秒</span>
        </p>
      </div>
      <!-- /排行倒计时 -->

      <!-- 票数排行榜 -->
      <div class="ranking_of_votes">
        <div class="NumberVotes">拍数排行榜</div>
        <div class="ranking_of_votes_box">
          <div class="Top_three">
            <div class="Top_one">
              <span class="Top_one_span1">No.2</span>
              <img src="http://img4.imgtn.bdimg.com/it/u=11990170,1283829948&fm=11&gp=0.jpg" alt />
              <span class="Top_one_span2">王一博</span>
              <span class="Top_one_span3">8888票</span>
            </div>
            <div class="Top">
              <span class="Top_one_span1">
                <img
                  src="http://img4.imgtn.bdimg.com/it/u=2456257843,433815831&fm=26&gp=0.jpg"
                  alt
                  class="imgtop"
                />
              </span>
              <img
                class="img"
                src="http://img0.imgtn.bdimg.com/it/u=3121987967,617912137&fm=26&gp=0.jpg"
                alt
              />
              <span class="Top_one_span2">彭于晏</span>
              <span class="Top_one_span3">9999票</span>
            </div>
            <div class="Top_one">
              <span class="Top_one_span1">No.3</span>
              <img src="http://img3.imgtn.bdimg.com/it/u=3534940287,477709860&fm=26&gp=0.jpg" alt />
              <span class="Top_one_span2">肖战</span>
              <span class="Top_one_span3">7777票</span>
            </div>
          </div>
          <ul class="Top_list">
            <li class="Top_list_li">
              <div class="Top_list_li_div">
                <img
                  src="http://img1.imgtn.bdimg.com/it/u=2585320048,2410615225&fm=26&gp=0.jpg"
                  alt
                />
                <div>
                  <p>华晨鱼</p>
                  <p>2123票</p>
                </div>
              </div>
              <span>4</span>
            </li>
            <li class="Top_list_li">
              <div class="Top_list_li_div">
                <img
                  src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3694987342,3950601598&fm=26&gp=0.jpg"
                  alt
                />
                <div>
                  <p>华晨鱼</p>
                  <p>2123票</p>
                </div>
              </div>
              <span>5</span>
            </li>
            <li class="Top_list_li">
              <div class="Top_list_li_div">
                <img
                  src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3133352696,3760892022&fm=26&gp=0.jpg"
                  alt
                />
                <div>
                  <p>华晨鱼</p>
                  <p>2123票</p>
                </div>
              </div>
              <span>6</span>
            </li>
            <li class="Top_list_li">
              <div class="Top_list_li_div">
                <img
                  src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=4169369728,2337319514&fm=26&gp=0.jpg"
                  alt
                />
                <div>
                  <p>华晨鱼</p>
                  <p>2123票</p>
                </div>
              </div>
              <span>7</span>
            </li>
            <li class="Top_list_li">
              <div class="Top_list_li_div">
                <img
                  src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3749120492,629625656&fm=26&gp=0.jpg"
                  alt
                />
                <div>
                  <p>华晨鱼</p>
                  <p>2123票</p>
                </div>
              </div>
              <span>8</span>
            </li>
            <li class="Top_list_li">
              <div class="Top_list_li_div">
                <img
                  src="https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=108891907,3028860246&fm=26&gp=0.jpg"
                  alt
                />
                <div>
                  <p>华晨鱼</p>
                  <p>2123票</p>
                </div>
              </div>
              <span>9</span>
            </li>
          </ul>
        </div>
      </div>
      <!-- /票数排行榜 -->
    </div>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      day: "0",
      hour: "00",
      min: "00",
      second: "00"
    };
  },
  computed: {},
  created() {
    this.countTime();
  },
  mounted() {},
  watch: {},
  methods: {
    countTime() {
      var endTime = "2020-11-11 00:00:00";
      var newTime = endTime.replace(/-/g, "/");
      var endDate = new Date(newTime);

      var thiss = this;
      setInterval(function() {
        var startDate = new Date();
        var totalSecond = (endDate - startDate) / 1000; //计算时间差
        var Sday = parseInt(totalSecond / 60 / 60 / 24);
        var Shouer = parseInt((totalSecond / 60 / 60) % 24);
        var Sminute = parseInt((totalSecond / 60) % 60);
        var Ssecond = parseInt(totalSecond % 60);

        thiss.day = Sday;
        thiss.hour = Shouer;
        thiss.min = Sminute;
        thiss.second = Ssecond;
      }, 1000);
    }
  },
  components: {}
};
</script>

<style >
.box {
  background-color: rgb(245, 245, 245);
}
.box1 {
  margin: 0 30rpx 120rpx 30rpx;
}
/* 排行榜倒计时 */
.paiha_time {
  text-align: center;
  padding: 40rpx;
  color: #777777;
}
.paiha_time_p {
  margin-bottom: 10rpx;
}
/* /排行榜倒计时 */

/* 票数排行榜 */
.ranking_of_votes {
  background-color: white;
}
.ranking_of_votes_box {
  padding: 0 30rpx;
  /* border: 1rpx solid rgb(245, 245, 245); */
}
.NumberVotes {
  background-color: rgb(48, 200, 179);
  text-align: center;
  padding: 20rpx;
  color: white;
}
.Top_three {
  padding: 30rpx 0rpx;
  width: 100%;
  display: flex;
}
.Top_one {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25rpx;
  width: 30%;
  margin-top: 30rpx;
}
.Top_one img {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}
.Top_one_span1 {
  color: salmon;
}
.Top_one_span2 {
  color: #777777;
  margin: 10rpx;
}
.Top_one_span3 {
  color: rgb(48, 200, 179);
}
.Top {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 15rpx;
  width: 30%;
}
.Top .img {
  width: 150rpx;
  height: 150rpx;
  margin: 20rpx;
  border-radius: 50%;
  border: 1px solid rgb(223, 223, 1);
  z-index: 10;
}
.Top .imgtop {
  width: 70rpx;
  height: 70rpx;
  margin: -20rpx 0 -45rpx -50rpx;
}
.Top_list {
}
.Top_list_li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20rpx;
  border-top: 1rpx solid rgb(245, 245, 245);
  border-bottom: 1rpx solid rgb(245, 245, 245);
}
.Top_list_li img {
  width: 100rpx;
  height: 100rpx;
  margin: 20rpx;
  border-radius: 50%;
}
.Top_list_li_div {
  display: flex;
  align-items: center;
  font-size: 20rpx;
  color: #777777;
}
.Top_list_li_div p {
  margin-bottom: 10rpx;
}
/* /票数排行榜 */
</style>
