<template>
  <div :class="$style.header">
    <span :class="$style.left">
      <router-link to="/login">登录</router-link>&nbsp;|&nbsp;
      <router-link to="/regist">注册</router-link>
    </span>
    <btn :class="$style.btnDown">APP下载</btn>
  </div>
</template>

<script>
import btn from '../base/btn'
  export default {
    components: {
      btn
    }
  }
</script>

<style lang ="scss" module>
.header{
  color: #666;
  height: 100px;
  line-height: 100px;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  font-size: 32px;
  background: #fff url(//m.jr.jd.com/spe/qyy/main/images/jr-logo.png) center center no-repeat;
  background-size: auto 50%;
  z-index: 100;
  & span a{
    color: #666;
    text-decoration: none;
  }
  .left{
    font-size: 28px;
    height: 30px;
    line-height: 30px;
    margin: 17px 0 0 18px; 
  }
  .btnDown{
    float: right;
    font-size: 24px;
    border-width: 0;
    height: 56px;
    line-height: 56px;
    min-width: 120px;
    padding: 0;
    border-radius: 4px;
    margin: 28px 24px 0 0;
  }
}
</style>