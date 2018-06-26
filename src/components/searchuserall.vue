<template>
    <div>
        <heador class="header"></heador>
        <div class="content">
            <div class="con_inner">
            <div class="con_nav">
                <div class="con_nav_l">
                <h3>Address</h3>
                <span>{{this.$route.query.orderId}}</span>
                </div>
                 <div class="con_nav_r">
                <ul>
                    <li @click="goback">Home&nbsp;/&nbsp;</li>
                    <li>Address</li>
                </ul>
                </div>
            </div>
            <div class="con_mid">
               
  <el-table
    :data="tableData.data"
    style="width: 100%">
    <el-table-column
      label="TxHash"
      min-width="20%">
      <template slot-scope="scope">
        <span class="span_text"><em><router-link :to="{ path: '/searchorder', query: { orderId: scope.row.transactionCode }}">{{ scope.row.transactionCode }}</router-link></em></span>
      </template>
    </el-table-column>
    <el-table-column
      label="Age"
      min-width="20%">
      <template slot-scope="scope">
        <span class="span_text">{{ scope.row.time }}</span>
      </template>
    </el-table-column>
    <el-table-column
      label="From"
      min-width="20%">
      <template slot-scope="scope">
        <span class="span_text"><em><router-link :to="{ path: '/searchuserall', query: { orderId: scope.row.fromToken }}">{{ scope.row.fromToken }}</router-link></em></span>
        <!-- <span class="span_text" @click="tdzz(scope.row.fromToken)"><em>{{ scope.row.fromToken }}</em></span> -->
      </template>
    </el-table-column>
    <el-table-column
      label="To"
      min-width="20%">
      <template slot-scope="scope">
         <span class="span_text"><em><router-link :to="{ path: '/searchuserall', query: { orderId: scope.row.toToken }}">{{ scope.row.toToken  }}</router-link></em></span>
        <!-- <span class="span_text" @click="tdzz(scope.row.toToken)"><em>{{ scope.row.toToken }}</em></span> -->
      </template>
    </el-table-column>
    <el-table-column
      label="Value"
      min-width="20%">
      <template slot-scope="scope">
        <span class="span_text">{{ scope.row.amount/10}}</span>
      </template>
    </el-table-column>
    <!-- <el-table-column
      label="[TxFee]"
      min-width="20%">
       <template slot-scope="scope">
          <span class="span_text">{{ scope.row.TxFee }}</span>
      </template> 
    </el-table-column> -->
  </el-table>
            </div>
            </div>
            <div class="fyq">
  <el-pagination
  background
  layout="total,prev, pager, next"
  :page-size="4"
  @current-change="handleCurrentChange"
  :current-page.sync="currentPage1"
  :total=  tableData.total>
</el-pagination>
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
      tableData:{},
      newdata: "",
      currentPage1: 1,
      curpage: 1
    };
  },
  components: {
    heador,
    footer1
  },
  watch: {
    '$route': 'getdata'
  },
  mounted() {
    console.log(this.$route.query.orderId)
    this.getdata();
  },
  methods: {
     handleCurrentChange(val) {
      //console.log(`当前页: ${val}`);
      this.curpage = val;
      console.log(this.curpage)
      this.getdata();
       //$(window).scrollTop(0);
         $('html,body').animate({scrollTop: '0px'}, 800); 
    },
    goback() {
      this.$router.push("/");
    },
    // tdzz(val){
    //     this.$router.push({path: '/searchuserall', query: {orderId: val}});
    //     this.getdata();
    // },
    getdata() {
      $('html,body').animate({scrollTop: '0px'},0); 
      let vm = this;
       $.ajax({
        url: "http://123.206.80.238:8092/ttc-eggworld-browser/browser/transaction/token/list?",
        type: "get",
        data: {
          page: vm.curpage,
          rows: 4,
          token: vm.$route.query.orderId
        },
        dataType: "json",
        success: function(data) {
           if (data.state.code == 20000) {
            // 交易记录
            vm.tableData = data;
            console.log(data)
            //console.log(data)
          }else if(data.state.code == 20001){
            vm.tableData = data;
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
          color: #777;
          cursor: pointer;
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
      span {
        height: 30px;
        line-height: 30px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        em{
            color: #3498db;
            a{
              text-decoration: none;
              color: deepskyblue;
            }
        }
      }
    }
  }
  .fyq {
    text-align: center;
    width: 100%;
    padding: 50px;
  }
}
</style>