<template>
  <div class="wrap1">
    <div class="list_header">
      <span class="title">
        Blocket
      </span>
      <a href="javascript:;" class="viewAll" @click="showmore">{{this.$t('moredata.more1')}}</a>
    </div>
    <div class="list_items">
      <list-item></list-item>
    </div>
  </div>
</template>

<script>
import listItem from "../base/listItem";
export default {
  data() {
    return {
      //more1: 
    };
  },
  components: {
    listItem
  },
  methods: {
    showmore(){
      this.$router.push({path:"/showmore"})
    }
  },
};
</script>

<style scoped lang="scss">
.wrap1{
  width: 695px;
  float: left;
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
}
</style>