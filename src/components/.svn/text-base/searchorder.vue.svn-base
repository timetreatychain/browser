<template>
    <div>
        <heador class="header"></heador>
        <div class="content">
            <div class="con_inner">
            <div class="con_nav">
                <div class="con_nav_l">
                <h3>Transaction</h3>
                <span>{{this.$route.query.orderId}}</span>
                </div>
                 <div class="con_nav_r">
                <ul>
                    <li @click="goback">Home&nbsp;/&nbsp;</li>
                    <li>Transactions</li>
                </ul>
                </div>
            </div>
            <div class="con_mid">
                <div class="con_mid_l">TxHash:</div>
                <div class="con_mid_r">{{this.$route.query.orderId}}</div>
                <div class="con_mid_l">TxReceipt Status:</div>
                <div class="con_mid_r">{{this.tableData.state}}</div>
                <!-- <div class="con_mid_l">TxReceipt Status:</div>
                <div class="con_mid_r"><em>5329790</em>(1 block confirmation)</div> -->
                <div class="con_mid_l">TimeStamp:</div>
                <div class="con_mid_r">{{this.tableData.time}}</div>
                <div class="con_mid_l">From:</div>
                <div class="con_mid_r"><em>{{this.tableData.fromToken}}</em></div>
                <div class="con_mid_l">To:</div>
                <div class="con_mid_r"><em>{{this.tableData.toToken}}</em></div>
                <!-- <div class="con_mid_l">Token Transfer:</div>
                <div class="con_mid_r"> 30<em> ERC20 (Decentralized Contract Chain Token)</em>  from <em>0x01b841d8a0c3f620125becd772c512a183276a46 </em>to <em> 0x936e104a2d7c51457b9052a18980c59060753597</em></div> -->
            </div>
            </div>
        </div>
        <footer1></footer1>
    </div>
</template>

<script>
import heador from "../base/header";
import footer1 from "../base/footer";
export default {
  data() {
    return {
      tableData: {}
    };
  },
  components: {
    heador,
    footer1
  },
  mounted() {
    //console.log(this.$route.query.order1)
    this.getdata();
  },
  methods: {
    goback() {
      this.$router.push("/");
    },
    getdata() {
      $('html,body').animate({scrollTop: '0px'},0); 
      let vm = this;
      $.ajax({
        url: "http://123.206.80.238:8092/ttc-eggworld-browser/browser/transaction/detail?",
        type: "get",
        data: {
          transactionCode: vm.$route.query.orderId
        },
        dataType: "json",
        success: function(data) {
          if (data.state.code == 20000) {
            // 流水记录
            vm.tableData = data.data;
          }else if (data.state.code == 20001) {
            // 流水记录
            vm.tableData = data.data;
          }
          
        },
        error: function(data) {
          console.log(data);
          alert("error !");
        }
      });
    }
  }
};
</script>

<style scoped lang="scss">
.header {
  position: sticky;
  top: 0;
  z-index: 99999;
  width: 100%;
}
.content {
  width: 100%;
  box-sizing: border-box;
  //padding-top: 302px;
  .con_inner {
    width: 90%;
    margin: 0 auto;
    .con_nav {
      background: #eee;
      height: 80px;
      padding-left: 10px;
      padding-right: 10px;
      line-height: 80px;
      .con_nav_l {
        float: left;
        h3 {
          color: #777;
          float: left;
          font-size: 20px;
        }
        span {
          float: left;
          font-size: 18px;
          padding-left: 10px;
          color: #999999;
        }
      }
      .con_nav_r {
        float: right;
        & ul li {
          float: left;
          font-size: 16px;
          cursor: pointer;
          color: #777;
          &:nth-child(2) {
            color: #3498db;
          }
        }
      }
    }
    .con_mid {
      border: solid 1px #3498db;
      overflow: hidden;
      margin-bottom: 20px;
      padding-right: 10px;
      margin-top: 20px;
      .con_mid_l {
        float: left;
        width: 30%;
        font-size: 18px;
        height: 60px;
        line-height: 60px;
        text-indent: 20px;
        // em {
        //   color: #3498db;
        // }
      }
      .con_mid_r {
        float: left;
        width: 70%;
        height: 60px;
        line-height: 60px;
        font-size: 16px;
        word-break: break-all;
        text-indent: 20px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        // em {
        //   color: #3498db;
        // }
      }
    }
  }
}
</style>