<template>
  <div class="goodsdesc-container">
    <h3>{{ info.title }}</h3>
    <hr>
    <div class="content" v-html="info.content"></div>
    <div class="img_wrap">
    <img :src="info.src"/>
    </div>
  </div>
</template>

<script>
import goodsdescjson from "../../json/goodsdesc.json";
export default {
  data() {
    return {
      info: {} // 图文数据
    };
  },
  created() {
    this.getGoodsDesc();
  },
  methods: {
    getGoodsDesc() {
    //   this.$http
    //     .get("api/goods/getdesc/" + this.$route.params.id)
    //     .then(result => {
    //       if (result.body.status === 0) {
    //         this.info = result.body.message[0];
    //       }
    //     });
    goodsdescjson.message.forEach((v,i)=>
    {
        if(v.id==this.$route.params.id){
            console.log(v);
            this.info=v;
            console.log(this.info.src);
        }
    });
    }
  }
};
</script>

<style lang="scss">
.goodsdesc-container {
  padding: 4px;
  h3 {
    font-size: 16px;
    color: #226aff;
    text-align: center;
    margin: 15px 0;
  }
  .content{
      margin:8px auto;
    img{
      width: 100%;
    }
  }
  .img_wrap{
      display:flex;
      justify-content:center;
      align-items:center;
      img{
          width:100%;
      }
  }
}
</style>
