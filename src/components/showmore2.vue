<template>
<div>
  <heador class="header"></heador>
  <div class="nav_bar">
    <a href="javascript:;" @click="goback">Home&nbsp;/</a>
    <a href="javascript:;">Transactions</a>
  </div>
<div class="listshow">
<el-table
    :data="tableData.data"
    style="width: 100%">
    <el-table-column
      width="500">
      <template slot-scope="scope">
        <!-- <i class="el-icon-time"></i>
        <span style="margin-left: 10px">{{ scope.row.date }}</span> -->
        <div class="list_item_l">
            <!-- <p>{{scope.row.preson.wz}} <em>{{scope.row.preson.preson_name}}</em></p>
            <p><em>{{scope.row.second.num}}</em>To <em> {{scope.row.second.last}}</em></p>
            <p>{{scope.row.third}}</p> -->
            <p>TX#<em><router-link :to="{ path: '/searchorder', query: { orderId: scope.row.transactionCode }}">{{scope.row.transactionCode}}</router-link></em></p>
            <p><em><router-link :to="{ path: '/searchuserall', query: { orderId: scope.row.fromToken }}">{{scope.row.fromToken}}</router-link></em>To <em><router-link :to="{ path: '/searchuserall', query: { orderId: scope.row.toToken }}"> {{scope.row.toToken}}</router-link></em></p>
            <p>Amount {{scope.row.amount /10}}TTC</p>
        </div>
      </template>
    </el-table-column>
    <el-table-column
      width="500">
      <template slot-scope="scope">
        <div class="list_item_r">
            <!-- <p>>{{scope.row.time}}</p> -->
             <p>>{{scope.row.time}}</p>
        </div>
      </template>
    </el-table-column>
  </el-table>
  <div class="fyq">
  <el-pagination
  background
  layout="total,prev, pager, next"
  :page-size="5"
  @current-change="handleCurrentChange"
  :current-page.sync="currentPage2"
  :total=  tableData.total>
</el-pagination>
</div>
</div>
<footer1 class="footer"></footer1>
</div>
</template>
<script>
import heador from "../base/header";
import footer1 from "../base/footer";
export default {
  data() {
    return {
      currentPage2: 1,
      tableData: {},
      curpage: 1
    };
  },
  mounted() {
    this.getData();
  },
  methods: {
    handleCurrentChange(val) {
      //console.log(`当前页: ${val}`);
      this.curpage = val;
      //console.log(this.curpage)
      this.getData();
       //$(window).scrollTop(0);
         $('html,body').animate({scrollTop: '0px'}, 800); 
    },
    goback() {
      this.$router.push("/");
    },
    getData() {
      let vm = this;
      $.ajax({
        url: "http://123.206.80.238:8092/ttc-eggworld-browser/ttc-eggworld/browser/transaction/list?",
        data: {
          page: vm.curpage,
          rows: 5
        },
        type: "get",
        dataType: "json",
        success: function(data) {
          //console.log(data)
          if (data.state.code == 20000) {
            vm.tableData = data;
            //console.log(data);
          }
          //alert(data)
        },
        error: function(data) {
          console.log(data);
          alert("error !");
        }
      });
    }
  },
  components: {
    heador,
    footer1
  }
};
</script>


<style scoped lang="scss">
.header {
  position: sticky;
  top: 0;
  z-index: 99999;
}
.nav_bar {
  height: 80px;
  background-color: #f7f7f7;
  width: 1000px;
  margin: 0 auto;
  font-size: 18px;
  line-height: 80px;
}
.nav_bar a {
  color: #000;
  display: block;
  width: 50px;
  float: left;
  padding-left: 20px;
  text-decoration: none;
  text-align: center;
  &:nth-child(2) {
    color: blue;
  }
}
.listshow {
  width: 1000px;
  //height: 700px;
  margin: 0 auto;
  padding-bottom: 30px;

  tr {
    width: 100%;
    position: relative;
    .list_item_r {
      width: 100%;
      position: absolute;
      top: 10px;
      right: 15px;
      box-sizing: border-box;
      //width: 30%;
      & p:nth-of-type(1) {
        width: 100%;
        font-size: 16px;
        color: #6e6e6e;
        word-break: break-all;
        margin-bottom: 6px;
        text-align: right;
      }
    }
    .list_item_l {
      float: left;
      width: 100%;
      p {
        font-size: 18px;
        margin-bottom: 16px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        line-height: 30px;
        em {
          display: inline-block;
          color: #465ef3;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
          vertical-align: top;
          a{
            color: deepskyblue;
            text-decoration: none;
          }
        }
        &:nth-child(2) em{
        width: 45%;
      }
      }
      
    }
  }
  .fyq {
    text-align: center;
    width: 100%;
    padding-top: 50px;
  }
  .footer {
    clear: both;
  }
}
</style>