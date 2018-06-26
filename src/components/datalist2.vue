<template>
  <div>
    <div class="list_header">
      <span class="title">
        Transactions
      </span>
      <a href="javascript:;" class="viewAll" @click="showmore">{{this.$t('moredata.more1')}}</a>
    </div>
    <div class="list_items">
      <list-item2></list-item2>
    </div>
  </div>
</template>

<script>
import listItem2 from "../base/listItem2";
export default {
  data() {
    return {

    };
  },
  components: {
    listItem2
  },
  methods: {
    showmore(){
      this.$router.push({path:"/showmore2"})
    }
  }
};
</script>

<style scoped lang="scss">
.list_header {
  width: 695px;
  height: 72px;
  //line-height: 72px;
  box-sizing: border-box;
  background-color: #eaeaea;
  overflow: hidden;
  padding: 14px 26px;
  .title {
    font-size: 20px;
    float: left;
    line-height: 44px;
    height: 44px;
  }
  .viewAll {
    float: right;
    width: 98px;
    height: 44px;
    text-align: center;
    line-height: 44px;
    font-size: 18px;
    text-decoration: none;
    color: #181818;
    border: solid 1px #181818;
    border-radius: 6px;
  }
   .viewAll:hover{
    background: #000;
    color: wheat;
  }
  
}
</style>