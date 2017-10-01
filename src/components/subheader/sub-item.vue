<template>
  <div class="sub-item">
    <div class="sub-item-logo">
      <div :class="`sub-item-logo-img sub-item-logo-img-${item.icon}`"></div>
    </div>
    <div class="sub-item-title">{{ item.title }}</div>
    <div class="sub-item-desc" v-html="item.desc"></div>
  </div>
</template>

<script>
  export default {
    props: {
      item: {
        type: Object,
        default: {}
      }
    },
    data () {
      return {}
    },
    methods: {}
  }
</script>

<style lang="less" rel="stylesheet/less" scoped>

  .sub-item {
    width: 50%;
    position: relative;
    margin-top: 60px;
    padding-bottom: 30px;
    &:before {
      position: absolute;
      content: '';
      display: block;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      background: #F66039;
      width: 20px;
      height: 2px;
    }
    &:nth-child(odd):after {
      position: absolute;
      content: '';
      display: block;
      right: 0;
      top: 50%;
      transform: translateY(-50%);
      background: #F0F0F0;
      width: 1px;
      height: 100%;
    }
  }
  .sub-item-logo {
    height: 70px;
    .sub-item-logo-img{
      height: 100%;
      background-size: auto 70px;
      background-repeat: no-repeat;
      background-position: center center;
    }
    .sub-item-logo-img-2{
      background-image: url(../../style/images/icon/icon-2.png);
    }
    .sub-item-logo-img-3{
      background-image: url(../../style/images/icon/icon-3.png);
    }
    .sub-item-logo-img-4{
      background-image: url(../../style/images/icon/icon-4.png);
    }
    .sub-item-logo-img-5{
      background-image: url(../../style/images/icon/icon-5.png);
    }
    .sub-item-logo-img-7{
      background-image: url(../../style/images/icon/icon-7.png);
    }
    .sub-item-logo-img-8{
      background-image: url(../../style/images/icon/icon-8.png);
    }
    .sub-item-logo-img-9{
      background-image: url(../../style/images/icon/icon-9.png);
    }
    .sub-item-logo-img-10{
      background-image: url(../../style/images/icon/icon-10.png);
    }
  }
  .sub-item-title {
    color: #000000;
    font-size: 28px;
    line-height: 40px;
    margin-top: 30px;
  }
  .sub-item-desc {
    line-height: 28px;
    font-size: 20px;
    color: #808080;
    margin-top: 15px;
  }
</style>
