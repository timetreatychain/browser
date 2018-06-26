<template>
    <div>
        <div class="footer">
            <div class="footer_inner">
            <div class="footer_l">
                <p>{{this.$t('linkinfo.text')}}</p>
                <p>{{this.$t('linkinfo.emailadress')}}：<a>TTC@timetreaty.org</a></p>
            </div>
            <div class="footer_r">
                <ul>
                    <li>
                        <img src="../assets/img/ewm_11.jpg" alt="">
                        <p>Facebook</p>
                    </li>
                    <li>
                        <img src="../assets/img/ewm_11.jpg" alt="">
                        <p>Telegram</p>
                    </li>
                    <li>
                        <img src="../assets/img/ewm_11.jpg" alt="">
                        <p>Twitter</p>
                    </li>
                </ul>
            </div>
            <p class="bq">&copy;2017 时间条约链 Time Treaty Chain</p>      
        </div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>

<style scoped lang="scss">
.footer {
  clear: both;
  width: 100%;
  height: 481px;
  background-color: #1b1b1b;
  padding-top: 108px;
  //padding-top: 32px;
  box-sizing: border-box;
  overflow: hidden;
  .footer_inner {
    width: 1462px;
    margin: 0 auto;
    overflow: hidden;

    .footer_l {
      float: left;
      width: 520px;
      padding-top: 42px;
      p {
        color: #ffbb00;
        font-size: 30px;
        word-break: break-all;
        height: 34px;
        margin-bottom: 30px;
        a {
          text-decoration: underline;
        }
      }
    }
    .footer_r {
      float: right;
      ul li {
        width: 162px;
        height: 202px;
        float: left;
        margin-right: 68px;
        img {
          width: 100%;
          height: 160px;
        }
        p {
          height: 42px;
          line-height: 42px;
          text-align: center;
          color: white;
          font-size: 28px;
        }
      }
    }
    p.bq {
      clear: both;
      width: 100%;
      height: 19px;
      font-family: MicrosoftYaHei;
      font-size: 16px;
      font-weight: normal;
      font-stretch: normal;
      line-height: 0px;
      letter-spacing: 0px;
      color: #ffffff;
      text-align: center;
      padding-top: 97px;
    }
  }
}
</style>