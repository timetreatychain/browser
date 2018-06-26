<template>
<div class="wrap">
    <div class="list_item" v-if="index < 5"  v-for="(item, index) in listitems1" :key="index">
        <div class="list_item_l">
            <p>TX#<em><router-link :to="{ path: '/searchorder', query: { orderId: item.transactionCode }}">{{item.transactionCode}}</router-link></em></p>
            <p><em><router-link :to="{ path: '/searchuserall', query: { orderId: item.fromToken }}">{{item.fromToken}}</router-link></em>To <em> <router-link :to="{ path: '/searchuserall', query: { orderId: item.toToken }}">{{item.toToken}}</router-link></em></p>
            <p>Amount {{item.amount/10}}TTC</p>
        </div>
        <div class="list_item_r">
            <p>>{{item.time}}</p>
        </div>

    </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      listitems1: {}
    };
  },
  mounted() {
    this.getData1();
  },
  methods: {
    getData1() {
      let vm = this;
      $.ajax({
        url:
          "http://123.206.80.238:8092/ttc-eggworld-browser/browser/transaction/list?page=1&rows=10",
        type: "get",
        dataType: "json",
        success: function(data) {
          //console.log(data)
          if(data.state.code == 20000){
            vm.listitems1 = data.data;
          //console.log(data.data);
          }
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
a{
  text-decoration: none;
}
.wrap {
  width: 695px;
  .list_item {
    position: relative;
    width: 695px;
    height: 134px;
    padding: 25px 26px 24px 26px;
    box-sizing: border-box;
    background-color: #f7f7f7;
    box-shadow: 0 10px 5px #eee;
    margin-bottom: 5px;
    .list_item_r {
      position: absolute;
      right: 8px;
      box-sizing: border-box;
      width: 30%;
      & p:nth-of-type(1) {
        font-size: 16px;
        color: #6e6e6e;
        word-break: break-all;
        margin-bottom: 6px;
        text-align: right;
      }
    }
    .list_item_l {
      float: left;
      width: 70%;
      p {
        font-size: 18px;
        margin-bottom: 16px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        em {
          display: inline-block;
          color: #465ef3;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
          vertical-align: top;
          a{
            color: deepskyblue;
          }
        }
        &:nth-child(2) em{
        width: 45%;
      }
      }
      
    }
    &:last-child {
      box-shadow: none;
    }
  }
}
</style>