<template>
<div>
  <heador class="header"></heador>
  <div class="nav_bar">
    <a href="javascript:;" @click="goback">Home&nbsp;/</a>
    <a href="javascript:;">Blocket</a>
  </div>
<div class="listshow">
<el-table
    :data="tableData.data"
    style="width: 100%">
    <el-table-column
      width="300">
      <template slot-scope="scope">
        <div class="list_item_l">
            <!-- <p>{{scope.row.number}}</p>
            <p>>{{scope.row.time}}</p> -->
            <p>block:{{scope.row.blockId}}</p>
            <p>{{scope.row.createTime }}</p>
        </div>
      </template>
    </el-table-column>
    <el-table-column
      width="700">
      <template slot-scope="scope">
        <div class="list_item_r">
            <!-- <p>{{scope.row.preson.wz}} <em>{{scope.row.preson.preson_name}}</em></p>
            <p><em>{{scope.row.second.num}}</em>{{scope.row.second.last}}</p>
            <p>{{scope.row.third}}</p> -->
             <p>Mined By:<em><router-link :to="{ path: '/searchuserall', query: { orderId:scope.row.token }}">{{scope.row.token}}</router-link></em></p>
            <p>TTC Code:{{scope.row.code}}</p> 
        </div>
      </template>
    </el-table-column>
  </el-table>
  <div class="fyq">
  <el-pagination
  background
  layout="total,prev, pager, next"
  :page-size="10"
  @current-change="handleCurrentChange"
  :current-page.sync="currentPage1"
  :total=  tableData.total>
</el-pagination>
</div>
</div>
<footer1></footer1>
</div>
</template>

<style scoped>

</style>

<script>
import heador from "../base/header";
import footer1 from "../base/footer";
export default {
  data() {
    return {
      currentPage1: 1,
      showmore: [],
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
      console.log(this.curpage)
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
        url:
          "http://123.206.80.238:8092/ttc-eggworld-browser/ttc-eggworld/browser/produce/list?",
        data:{
          page:vm.curpage,
          rows:10
        },
        type: "get",
        dataType: "json",
        success: function(data) {
          //console.log(data)
          if(data.state.code ==20000){
            vm.tableData = data;
            //console.log(data)
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
  z-index: 9999;
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
  padding-bottom: 30px;
  margin: 0 auto;
  .list_item_l {
      float: left;
      box-sizing: border-box;
      width: 220px;
      height: 85px;
      background-color: #dbdbdb;
      padding: 23px 20px;
      margin-right: 15px;
      & p:nth-of-type(1) {
        font-size: 20px;
        word-break: break-all;
        margin-bottom: 6px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
      & p:nth-of-type(2) {
        font-size: 18px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
  .list_item_r {
    float: left;
    p {
      font-size: 18px;
      margin-bottom: 16px;
      em {
        color: #465ef3;
        a{
          color: deepskyblue;
          text-decoration: none;
        }
      }
    }
  }
  .fyq {
    text-align: center;
    width: 100%;
    padding-top: 50px;
  }
}
</style>