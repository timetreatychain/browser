<template>
    <div>
        <h1 @click="goback"><a href="javascript:;"><img src="../assets/img/logo.jpg" alt=""></a></h1>
        <div class="header_r">
            <div class="search"><input id="searchtext" type="text" v-model.trim="msg" :placeholder="$t('placeholder.enter')"><span @click="searchinfo"><img src="../assets/img/search.jpg" alt=""></span></div>
            <div class="langue" @click="showlist">
                <a class="btnclick"  href="javascript:;"><i>English</i><em><img src="../assets/img/arrow.jpg" alt=""></em></a>
                <ul ref="list" class="list">
                    <li @click="changelang(1)" class="active"><a href="javascript:;">English</a></li>
                    <li @click="changelang(2)"><a href="javascript:;">简体中文</a></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      btnshow: false,
      flag: true,
      msg:""
    };
  },
  methods: {
    goback() {
      this.$router.push("/");
    },
    changelang(val) {
      let vm = this;
      if (val == 1) {
        window.localStorage.setItem('language', 'en')
        let locale = vm.$i18n.locale;
        vm.$i18n.locale = window.localStorage.getItem('language');
        eventBus.$emit("eventchange", "en");
        $(".list li").eq(0).addClass("active").siblings("li").removeClass("active");
        $(".btnclick i").html($(".list li").eq(0).children("a").html())
      } else {
        window.localStorage.setItem('language', 'zh')
        let locale = vm.$i18n.locale;
        vm.$i18n.locale = window.localStorage.getItem('language');
        eventBus.$emit("eventchange", "zh");
       $(".list li").eq(1).addClass("active").siblings("li").removeClass("active");
        $(".btnclick i").html($(".list li").eq(0).children("a").html());
        
      }
    },
    showlist() {
      let vm = this;
      this.btnshow = !this.btnshow;
      if (this.btnshow) {
        this.$refs.list.style.display = "block";
      } else {
        this.$refs.list.style.display = "none";
      }
      $(".list li").click(function() {});
    },
    searchinfo() {
      let vm = this;
      // this.flag = !this.flag;
      // if (this.flag) {
      //   this.$router.push({
      //     path: "/searchuserall",
      //     query: { order1: $("#searchtext").val() }
      //   });
      // } else {
      //   this.$router.push({
      //     path: "/searchorder",
      //     query: { order1: $("#searchtext").val() }
      //   });
      // }
      // $.ajax({
      //   url: "http://123.206.80.238:8090/ttc-eggworld/ttc/search/?",
      //   type: "get",
      //   data: {
      //     code: $("#searchtext").val()
      //   },
      //   dataType: "json",
      //   success: function(data) {
      //     if (data.state.code == 20000 && data.type == 0) {
      //       // 交易详情
      //       console.log(data);
      //       vm.$router.push({
      //         name: "searchorder",
      //         query: { orderId: data.data.transactionCode }
      //       });
      //       //eventBus.$emit("showdata1", data);
      //     } else if (data.state.code == 20000 && data.type == 1) {
      //       // 交易详情
      //       console.log(data);
      //       return;
      //       vm.$router.push({
      //         name: "searchuserall",
      //         query: { orderId: data.data }
      //       });
      //       //eventBus.$emit("showdata1", data);
      //     }
      //     //console.log(data)
      //     //vm.listitems = data;
      //     //console.log(vm.listitems);
      //     //console.log(data)
      //     //alert(data)
      //   },
      //   error: function(data) {
      //     console.log(data);
      //     alert("error !");
      //   }
      // });
      var vallen = this.msg;
      if (vallen.length > 34) {
        vm.$router.push({
          name: "searchorder",
          query: { orderId:  $("#searchtext").val() }
        });
      } else if(vallen.length <=34) {
        vm.$router.push({
          name: "searchuserall",
          query: { orderId:  $("#searchtext").val() }
        });
      }
    }
  }
};
</script>

<style scoped lang="scss">
.header {
  width: 100%;
  height: 152px;
  background: #1a1a1a;
  padding: 1px;

  h1 {
    width: 452px;
    height: 80px;
    margin: 36px 0px 0px 60px;
    float: left;
    a {
      width: 100%;
      height: 100%;
      display: block;
      img {
        width: 100%;
        //height: 100%;
        display: block;
      }
    }
  }

  .header_r {
    float: right;
    margin: 60px 60px 0 0;

    .search {
      float: left;
      margin-right: 92px;
      width: 498px;
      height: 48px;
      border-radius: 25px;
      background-color: #ffbb00;
      overflow: hidden;
      input {
        float: left;
        width: 90%;
        height: 100%;
        background-color: #ffbb00;
        outline: none;
        border: none;
        border-radius: 25px;
        color: #000000;
        text-indent: 20px;
        display: block;
      }

      span {
        float: right;
        width: 27px;
        height: 28px;
        margin: 11px 22px 0px 0px;
        img {
          width: 100%;
          display: block;
        }
      }
    }

    .langue {
      position: relative;
      z-index: 3;
      float: right;
      width: 155px;
      height: 32px;
      border-radius: 16px;
      border: solid 1px #ffffff;
      text-align: center;
      line-height: 30px;
      margin-top: 10px;
      font-family: "MicrosoftYaHei";

      .btnclick {
        display: block;
      }

      em {
        position: absolute;
        top: 11px;
        right: 8px;
        width: 19px;
        height: 11px;
        img {
          display: block;
          width: 100%;
        }
      }

      a {
        color: #fff;
        text-decoration: none;
        font-size: 18px;
      }

      ul {
        display: none;
        margin-top: 10px;
      }

      ul li {
        width: 100%;
        height: 56px;
        line-height: 56px;
        background: #0a0a0a;
      }

      ul li a {
        display: block;
      }

      ul li.active a {
        color: #ffbb00;
        background: #171717;
      }
    }
  }
}
</style>