<template>
  <div class="sub-header">
    <div class="sub-header-logo">
      <img v-if="sub_data.sub_logo=='icon-1.png'" src="../../style/images/icon/icon-1.png"/>
      <img v-if="sub_data.sub_logo=='icon-6.png'" src="../../style/images/icon/icon-6.png"/>
      <img v-if="sub_data.sub_logo=='icon-11.png'" src="../../style/images/icon/icon-11.png"/>
    </div>
    <div class="sub-header-title">
      <h3>{{sub_data.sub_title}}</h3>
      <div class="sub-header-title-s1">{{sub_data.sub_en_title}}</div>
    </div>
    <div class="sub-header-desc" v-if="sub_data.sub_desc">{{sub_data.sub_desc}}</div>
    <div class="sub-header-button" v-if="button">
      <button @click="openRegister(item)">点击申请</button>
    </div>
  </div>
</template>

<script>
  export default {
    props:{
      sub_data:{
        type:Object,
        default:{}
      },
      button:{
        type:Boolean,
        default:true
      },
      item:{
        type:Object,
        default:function () {
          return {};
        }
      }
    },
    data () {
      return {}
    },
    methods: {
      openRegister(){
        this.$emit('openRegister',this.item.type);
      }
    }
  }
</script>

<style lang="less" rel="stylesheet/less" scoped>
  .sub-header{
    text-align: center;
    .sub-header-logo{
      height: 42px;
      img{ height: 100% }
    }
    .sub-header-title{
      font-size: 0;
    }
    .sub-header-title h3{
      font-size: 48px;
      color: #000000;
      line-height: 68px;
      margin-top: 15px;
    }
    .sub-header-title-s1{
      background: #BEBEBE;
      border-radius: 40px;
      padding: 0 25px;
      display: inline-block;
      color: #fff;
      font-size: 14px;
      line-height: 20px;
      letter-spacing: 4.5px;
    }
    .sub-header-desc{
      line-height: 28px;
      color: #666666;
      font-size: 20px;
      margin-top: 10px;
    }
    .sub-header-button button{
      outline: none;
      width: 190px;
      line-height: 50px;
      height: 50px;
      text-align: center;
      color: #fff;
      margin-top: 30px;
      background-image: linear-gradient(-180deg, #F96A4C 0%, #F86036 100%);
      border: none;
      box-shadow: 0 2px 4px 0 #F66039, inset 0 1px 0 0 rgba(255,255,255,0.50);
      border-radius: 4px;
      font-size: 24px;
    }
  }
</style>
