<template>
  <div class="main" id="app">
    <div class="acquaintance">相识</div>
    <div class="time">
      <ul>
        <li class="days">
          <div>Days</div>
          <div>{{ days }}</div>
        </li>
        <li class="hours">
          <div>Hours</div>
          <div>{{ hours }}</div>
        </li>
        <li class="minute">
          <div>Minutes</div>
          <div>{{ minutes }}</div>
        </li>
        <li class="second">
          <div>Seconds</div>
          <div>{{ seconds }}</div>
        </li>
      </ul>
    </div>

    <div class="love" @click="choose">相恋</div>
    <div class="time">
      <ul>
        <li class="days">
          <div>Days</div>
          <div>{{ lovedays }}</div>
        </li>
        <li class="hours">
          <div>Hours</div>
          <div>{{ lovehours }}</div>
        </li>
        <li class="minute">
          <div>Minutes</div>
          <div>{{ loveminutes }}</div>
        </li>
        <li class="second">
          <div>Seconds</div>
          <div>{{ loveseconds }}</div>
        </li>
      </ul>
    </div>

    <div class="message">
      <p>突然很想你</p>
    </div>

    <!-- <el-dialog :visible.sync="centerDialogVisible" width="30%" center :show-close="false"
            :close-on-click-modal="false" :close-on-press-escape="false">
            <span>做我女朋友,好不好?</span>
            <span slot="footer" class="dialog-footer">
                <el-button @click="centerDialogVisible = false">拒绝</el-button>
                </el-button>
                <el-button type="primary" @click="agree">答应</el-button>
                </el-button>
            </span>
        </el-dialog> -->
  </div>
</template>


<script>
var _hmt = _hmt || [];
(function () {
  var hm = document.createElement("script");
  hm.src = "https://hm.baidu.com/hm.js?b8355e277764fa39008454937a81afe6";
  var s = document.getElementsByTagName("script")[0];
  s.parentNode.insertBefore(hm, s);
})();

export default {
  name: "Love",
  data() {
    return {
      FirstAcquaintanceTime: new Date(2022, 3, 28, 0, 9, 0),
      years: 0,
      months: 0,
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,

      loveTime: new Date(2022, 4, 20, 5, 20, 0),
      lovedays: 0,
      lovehours: 0,
      loveminutes: 0,
      loveseconds: 0,
      centerDialogVisible: false,
      ifagree: false,
    };
  },

  created() {
    this.getAcquaintanceTime();
    this.getLoveTime();
  },

  methods: {
    getAcquaintanceTime() {
      this.flag = setInterval(() => {
        var endDate = new Date(2022, 6, 21, 11, 7, 0);
        var dateDiff = endDate.getTime() - this.FirstAcquaintanceTime.getTime();
        this.days = Math.floor(dateDiff / (24 * 3600 * 1000));
        var remainTime = dateDiff % (24 * 3600 * 1000);
        this.hours = Math.floor(remainTime / (3600 * 1000));
        var remainTime1 = remainTime % (3600 * 1000);
        this.minutes = Math.floor(remainTime1 / (60 * 1000));
        var remainTime2 = remainTime1 % (60 * 1000);
        this.seconds = Math.round(remainTime2 / 1000);
      }, 1000);
    },
    getLoveTime() {
      this.flag = setInterval(() => {
        var endDate = new Date(2022, 6, 21, 11, 7, 0);
        var dateDiff = endDate.getTime() - this.loveTime.getTime();
        this.lovedays = Math.floor(dateDiff / (24 * 3600 * 1000));
        var remainTime = dateDiff % (24 * 3600 * 1000);
        this.lovehours = Math.floor(remainTime / (3600 * 1000));
        var remainTime1 = remainTime % (3600 * 1000);
        this.loveminutes = Math.floor(remainTime1 / (60 * 1000));
        var remainTime2 = remainTime1 % (60 * 1000);
        this.loveseconds = Math.round(remainTime2 / 1000);
      }, 1000);
    },
    choose() {
      console.log(this.ifagree);
      if (this.ifagree == false) this.centerDialogVisible = true;
    },
    agree() {
      this.centerDialogVisible = false;
      this.ifagree = true;
      this.loveTime = new Date();
      this.getLoveTime();
    },
  },
};
</script>







<style>
@font-face {
  font-family: "love";
  src: url(../font/FZYiHTJW-EB.TTF);
}

* {
  margin: 0;
  padding: 0;
}

.el-dialog.el-dialog--center {
  border-radius: 10px;
}

body {
  background: #949494;
}

li {
  list-style: none;
}

a {
  color: #fff;
  text-decoration: none;
}

.main {
  position: absolute;
  width: 100%;
  height: 100%;
  text-align: center;
  /* background-image: url(images/2.jpg);
        background-size: 100% 100%;
        background-repeat: no-repeat; */

  /* background: url(../image/3.png) center 25% no-repeat; */
  background-size: 80% auto;

  font-family: "love";
  color: #fff;
}

.main:before {
  background-size: 70% auto;
  width: 100%;
  height: 100%;
  content: ""; /* 这个不要漏了 */
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1; /*-1 可以当背景*/
  opacity: 0.5;
}

.acquaintance {
  margin-top: 10%;
  font-size: 45px;
  font-weight: 200;
}

.time {
  margin-top: 50px;
}

.time ul li {
  display: inline-block;
  margin-right: 2vw;
}

.time ul li:last-child {
  margin-right: 0vw;
}

.love {
  margin-top: 10%;
  font-size: 45px;
  font-weight: 200;
}

.findmore {
  margin-top: 5%;
}

.picture {
  position: absolute;
  top: 10px;
  left: 10%;
  z-index: 0;
}

.message {
  margin-top: 5%;
  font-size: 20px;
  font-weight: 200;
}
</style>