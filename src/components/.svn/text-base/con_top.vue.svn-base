<template>
  <div class="cont_top">
    <div class="cont_top_inner">
      <!-- <div class="cont_top_inner_title">
        <p>
          <a href="http://www.timetreaty.com/">
            <span>{{$t("message.title_l")}}</span>
            <span>COPYIRACK-JOIN THE COPYRGHT REVOLYIION-$10M+ ALREADY RAISED
              <em>-SECURE BONUS NOW!</em>
            </span>
          </a>
        </p>
      </div> -->
      <div class="view_data">
        <div class="view_data_l">
          <div class="view_data_l_t">
            <!-- <span class="earth_pic"></span> -->
            <!-- <div class="earth_pic__r">
                                <p>MARKET CAP OF $55.715 BLLON</p>
                                <p>$571.78 @ 0.09512 BTC/ETH<em>(-30.16%)</em></p>
                            </div> -->
          </div>
          <div class="view_data_l_b">
            <ul>
              <li v-for="(item,index) in earthdata" :key="index">{{item.placename}}
                <p>{{item.placedata}}
                  <em>{{item.precent}}</em>
                </p>
              </li>
              <!-- <li>LAST BLOCK <p>5039871 <em>(14.4s)</em></p></li>
                                    <li>LAST BLOCK <p>5039871 <em>(14.4s)</em></p></li>
                                    <li>LAST BLOCK <p>5039871 <em>(14.4s)</em></p></li> -->
            </ul>
          </div>

        </div>
        <div class="view_data_r">
          <!-- <span class="viewtab active" @click="daydata">{{this.$t('dateTimer.day')}}</span>
          <span class="viewtab" @click="weekdata">{{this.$t('dateTimer.lastweek')}}</span> -->
          <!-- <span class="viewtab active">{{this.$t('dateTimer.lastmon')}}</span> -->
          <!-- <span class="viewtab" @click="tmontdata">{{this.$t('dateTimer.lastthreemon')}}</span>
          <span class="viewtab" @click="hyearata">{{this.$t('dateTimer.hyear')}}</span>
          <span class="viewtab" @click="yeardata">{{this.$t('dateTimer.lastyear')}}</span> -->
          <div ref="viewshowpic" id="viewshowpic" class="viewshowpic" style="width: 100%;height:100%"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import echarts from "echarts";
export default {
  //props: ["earthdata"],
  mounted() {
    //this.setOption1(["星期一","星期二","星期三","星期四","星期五","星期六","星期日"],[10,36,58,14,20,86,89])
    // this.monthdata();
    this.getdata0();
    this.getdata();
  },
  data() {
    return {
      // dateTimer: {
      //  lastweek: this.$t('dateTimer.lastweek'),
      //  lastmon: this.$t('dateTimer.lastmon'),
      //  lastthreemon: this.$t('dateTimer.lastthreemon'),
      //  hyear: this.$t('dateTimer.hyear'),
      //  lastyear: this.$t('dateTimer.lastyear')
      //  },
      changglan: localStorage.getItem("changelan"),
      monthdata1:"",
      daysArr2: [],
      earthdata: [
        {
          price: 0,
          placename: "MARKET CAP OF $55.715",
          placedata: "￥ @ 0.09512 BIDT/BTC",
          precent: "-30.16%"
        },
        {
          placename: "LAST BLOCK",
          placedata: 0,
          precent: "(14.4s)"
        },
        {
          placename: "TRANSACTIONS",
          placedata: "155.92 M",
          precent: "（11.7TPS)"
        },
        {
          placename: "Hash Rate",
          placedata: "228,040,09 GH/",
          precent: "S"
        },
        {
          placename: "Network Difficulty",
          placedata: "2,799,00 TH",
          precent: ""
        }
      ],
    };
  },
  watch: {
    changglan(val) {
      // console.log(val);
    }
  },
  methods: {
    // getdata0
    getdata0() {
      let vm = this;
      $.ajax({
        // url: "http://123.206.80.238:8092/ttc-eggworld-browser/browser/overview",
        url: "http://123.206.80.238:8092/ttc-eggworld-browser/browser/overview",
        data: {
          
        },
        type: "get",
        dataType: "json",
        success: function(data) {
          //console.log(data)
          if (data.state.code == 20000) {
            console.log(data.data);
            vm.earthdata[1].placedata = data.data.lastBlock;
            vm.earthdata[0].precent = data.data.rise;
             vm.earthdata[0].placedata = " ￥"+ data.data.price + " @ " +  data.data.bidtBtcBi  +" BIDT/BTC  ";
            vm.earthdata[1].precent = "(" + data.data.seconds + "s)";
            vm.earthdata[2].placedata =  + data.data.transcations + "M";
            vm.earthdata[2].precent = "(" + data.data.tps + "TPS)";
            
            // vm.monthdata();
          }
          //alert(data)
        },
        error: function(data) {
          console.log(data);
          alert("error !");
        }
      });
    },


    // getdata
    getdata() {
      let vm = this;
      $.ajax({
        url: "http://123.207.171.234:8081/timetreaty_org/api/offering/getPrice",
        data: {
          
        },
        type: "get",
        dataType: "json",
        success: function(data) {
          //console.log(data)
          if (data.state.code == 20000) {
            // vm.tableData = data;
            // return;
            vm.monthdata1 = data.data;
            // console.log(vm.monthdata1);
            vm.monthdata();
          }
          //alert(data)
        },
        error: function(data) {
          console.log(data);
          alert("error !");
        }
      });
    },
    setOption1(data1, data2) {
      $(".viewshowpic div").css("top", "-20px");
      let vm = this;
      eventBus.$on("eventchange", function(val) {
        $(".view_data_r span")
          .eq(0)
          .addClass("active")
          .siblings(".viewtab")
          .removeClass("active");
        vm.weekdata();
      });
      $(".view_data_r span").click(function() {
        $(this)
          .addClass("active")
          .siblings(".viewtab")
          .removeClass("active");
      });
      let myChart = echarts.init(document.getElementById("viewshowpic"));
      var option = {
        tooltip: {},
        legend: {},
        xAxis: {
          splitLine: { show: true }, //去除网格线
          axisLine: { onZero: false },
          //data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
          data: data1
        },
        yAxis: {
          splitLine: { show: true }
        },
        color: "#ffbb00",
        series: [
          {
            // name: '销量',
            type: "line",
            data: data2
          }
        ]
      };

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },
    daydata() {
      var weeks = new Date().getHours();
      let daysArr = [];
      // let weeksArr2 = ["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
      let daysArr2 = this.$t("day.dayhour");
      for (let i = 0; i < 12; i++) {
        daysArr.unshift(daysArr2[weeks]);
        weeks--;
        if (weeks < 0) {
          weeks = 12;
        }
      }
      this.setOption1(daysArr, [
        45,
        36,
        58,
        14,
        20,
        86,
        89,
        45,
        36,
        58,
        14,
        20
      ]);
    },
    weekdata() {
      var weeks = new Date().getDay();
      let weeksArr = [];
      // let weeksArr2 = ["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
      let weeksArr2 = this.$t("weeks.weeksname");
      for (let i = 0; i < 6; i++) {
        weeksArr.unshift(weeksArr2[weeks]);
        weeks--;
        if (weeks < 0) {
          weeks = 6;
        }
      }
      this.setOption1(weeksArr, [0.1, 0.2, 0.15, 0.13, 0.21, 0.22, 0.21]);
    },
    monthdata() {
      var d = new Date();
      var days = new Date(d.getFullYear(), d.getMonth() + 1, 0).getDate();
      var predate = new Date(d.getFullYear(), d.getMonth(), 0).getDate();
      var nowdays = new Date().getDate();
      var dayArr = [];
      let daysArr2 = [];
      for (let i = 1; i <= 12; i++) {
        if (nowdays <= 0) {
          //console.log(nowdays)
          dayArr.unshift(predate);
          predate--;
          continue;
        }
        dayArr.unshift(nowdays);
        nowdays--;
      }
      this.monthdata1 &&  this.monthdata1.map( (item) => {
         this.daysArr2.push(item.pice)
       })
      this.setOption1(dayArr, this.daysArr2);
    },
    tmontdata() {
      var mArr = new Date().getMonth();
      let tmonthArr = [];
      for (let i = 0; i <= 2; i++) {
        if (mArr < 0) {
          mArr = 12;
        }
        tmonthArr.unshift(this.$t("months.monthsname")[mArr]);
        mArr--;
      }
      // this.setOption1([new Date().getMonth()-1+ "月",new Date().getMonth()+ "月",new Date().getMonth()+1+ "月"],[ 6, 50, 20])
      this.setOption1(tmonthArr, [6, 50, 20]);
    },
    hyearata() {
      var hyearstart = new Date().getMonth() + 1;
      let hyearArr = [];
      for (let i = 0; i < 6; i++) {
        if (hyearstart <= 0) {
          hyearstart = 12;
        }
        hyearArr.unshift(this.$t("months.monthsname")[hyearstart - 1]);
        hyearstart--;
      }
      this.setOption1(hyearArr, [30, 9, 30, 6, 50, 20]);
    },
    yeardata() {
      var hm = [];
      var m = new Date().getMonth() + 1;
      for (let i = 0; i < 12; i++) {
        //hm.unshift(m +"月");
        hm.unshift(this.$t("months.monthsname")[m - 1]);
        m--;
        if (m <= 0) {
          m = 12;
        }
      }
      this.setOption1(hm, [9, 30, 6, 50, 20, 10, 30, 9, 30, 6, 50, 20]);
    }
  }
};
</script>
<style lang="scss">
#viewshowpic {
  div {
    position: relative;
    top: -30px;
  }
}
</style>

<style scoped lang="scss">
.cont_top {
  //width: 1920px;
  width: 100%;
  height: 432px;
  box-sizing: border-box;
  padding-top: 34px;
  background-color: #f7f7f7;
  .cont_top_inner {
    width: 1464px;
    margin: 0 auto;

    .cont_top_inner_title {
      width: 100%;
      height: 28px;
      margin-bottom: 14px;
      p {
        font-family: "ArialMT";
        font-size: 18px;
        margin-bottom: 16px;
        a {
          text-decoration: none;
        }

        & span:nth-of-type(1) {
          margin-right: 30px;
          font-size: 18px;
        }

        em {
          color: #ffbb00;
          font-size: 18px;
        }
      }
    }

    .view_data {
      width: 100%;
      height: 300px;

      .view_data_l {
        float: left;
        //width: 695px;
        width: 45%;
        height: 100%;
        background-color: #262a42;
        box-sizing: border-box;
        padding: 20px 26px;
        overflow: hidden;
        .view_data_l_t {
          // overflow: hidden;
          .earth_pic {
            float: left;
            width: 105px;
            height: 100px;
            background: url("../assets/img/earth.jpg") left top no-repeat;
            background-size: 105px 100px;
            margin-right: 10px;
          }
          .earth_pic__r {
            float: left;
            & p:nth-of-type(1) {
              font-size: 18px;
              color: #ffbb00;
              margin-top: 15px;
              margin-bottom: 14px;
            }
            & p:nth-of-type(2) {
              font-size: 24px;
              color: #ffbb00;
              em {
                color: red;
                font-size: 16px;
              }
            }
            .viewshowpic div {
              width: 70%;
            }
          }
        }
        .view_data_l_b {
          padding-top: 20px;
          overflow: hidden;
          box-sizing: border-box;
          ul li {
            float: left;
            box-sizing: border-box;
            width: 46%;
            margin-bottom: 25px;
            color: #ffbb00;
            font-size: 18px;
            word-break: break-all;
            margin-left: 2%;
            p {
              font-size: 24px;
              margin-top: 5px;
              em {
                font-size: 16px;
              }
            }
          }
          ul li:nth-of-type(1) {
            height: 100px;
            width: 90%;
            background: url("../assets/img/earth.jpg") left top no-repeat;
            background-size: 105px 100px;
            padding-left: 120px;
            padding-top: 20px;
            em {
              color: red;
            }
          }
          ul li:nth-of-type(2) {
            clear: left;
          }
        }
      }
      .view_data_r {
        float: right;
        //width: 695px;
        width: 45%;
        height: 300px;
        box-sizing: border-box;
        padding: 20px 26px;
        border: 1px solid #000;
        span {
          position: relative;
          z-index: 999;
          float: left;
          display: block;
          border: 1px solid #d4d4d4;
          font-size: 16px;
          padding: 5px;
          margin-bottom: 5px;
          margin-right: 10px;
          border-radius: 4px;
          color: #666;
          cursor: pointer;
          &.active {
            background: #ffbb00;
            color: #000;
            border-color: transparent;
          }
        }
      }
    }
  }
}
</style>