<template>
<div class="wrap">
    <div class="list_item" v-if="index < 5"  v-for="(item, index) in listitems" :key="index">
        <div class="list_item_l">
            <p>block:{{item.blockId}}</p>
            <p>{{item.createTime }}</p>
        </div>
        <div class="list_item_r">
            <!-- <p>{{item.preson.wz}} <em>{{item.preson.preson_name}}</em></p>
            <p><em>{{item.second.num}}</em>{{item.second.last}}</p>
            <p>{{item.third}}</p> -->
            <p>Mined By:<em><router-link :to="{ path: '/searchuserall', query: { orderId:item.token }}">{{item.token}}</router-link></em></p>
            <p>TTC Code:{{item.code}}</p> 
        </div>
    </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      listitems:  { }
      
    };
  },
  mounted() {
    // let vm = this;
    this.getData();
    //  window.setInterval(function () {
    // console.log("这是轮询押");
    //  vm.getData();
    //    },10000);
  },
  methods: {
    getData() {
      let vm = this;
      $.ajax({
        url:
          "http://123.206.80.238:8092/ttc-eggworld-browser/browser/produce/list?page=1&rows=10",
        type: "get",
        dataType: "json",
        success: function(data) {
          if(data.state.code ==20000){
            vm.listitems = data.data;
          }
          //console.log(data)
          //vm.listitems = data;
          //console.log(vm.listitems);
          //console.log(data)
          //alert(data)
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
.wrap {
  //width: 695px;
  width: 100%;
  .list_item {
    //width: 695px;
    width: 100%;
    height: 134px;
    padding: 25px 26px 24px 26px;
    box-sizing: border-box;
    background-color: #f7f7f7;
    box-shadow: 0 10px 5px #eee;
    margin-bottom: 5px;
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
        width: 400px;
        font-size: 18px;
        margin-bottom: 16px;
        word-break: break-all;
        overflow: hidden;
        text-overflow: ellipsis;
        height: 30px;
        line-height: 30px;
        white-space: nowrap;
        em {
          color: #465ef3;
          a{
            color: deepskyblue;
            text-decoration: none;
          }
        }
      }
    }
    &:last-child {
      box-shadow: none;
    }
  }
}
</style>