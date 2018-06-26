<template>
    <div>
        <cont-top></cont-top>
        <cont-bot></cont-bot>
    </div>
</template>

<script>
import contTop from "./con_top";
import contBot from "./con_bot";
export default {
  data() {
    return {
      total1: 111,
      total2: 0,
      
    };
  },
  mounted() {
    // this.getData();
    // this.getData1();
  },
  watch:{
    //  total1(val) {
    //      this.earthdata[1].placedata = val
    //  },
    //  total2(val2) {
    //      this.earthdata[2].placedata = val2
    //  }  
  },
  methods: {
    // getData() {
    //   let vm = this;
    //   $.ajax({
    //     url: "http://123.206.80.238:8090/ttc-eggworld/browser/produce/list?",
    //     data: {
    //       page: 1,
    //       rows: 10
    //     },
    //     type: "get",
    //     dataType: "json",
    //     success: function(data) {
    //       //console.log(data)
    //       if (data.state.code == 20000) {
    //         vm.total1 = data.total;
    //         // console.log(vm.total1);
    //         //console.log(data)
    //       }
    //       //alert(data)
    //     },
    //     error: function(data) {
    //       console.log(data);
    //       alert("error !");
    //     }
    //   });
    // },
    //  getData1() {
    //   let vm = this;
    //   $.ajax({
    //     url: "http://123.206.80.238:8090/ttc-eggworld/browser/transaction/list?",
    //     data: {
    //       page: 1,
    //       rows: 5
    //     },
    //     type: "get",
    //     dataType: "json",
    //     success: function(data) {
    //       //console.log(data)
    //       if (data.state.code == 20000) {
    //         vm.total2 = data.total;
    //         console.log(vm.total2);
    //       }
    //       //alert(data)
    //     },
    //     error: function(data) {
    //       console.log(data);
    //       alert("error !");
    //     }
    //   });
    // }
  },
  components: {
    contTop,
    contBot
  }
};
</script>

<style scoped>
</style>