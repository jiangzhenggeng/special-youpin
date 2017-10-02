<template>
  <div class="content-wrap">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',

}
</script>

<style lang="less" rel="stylesheet/less">
  @import "style/less/base.less";
  .content-wrap{
    font-family: "SF Pro SC","HanHei SC","SF Pro Text","Myriad Set Pro","SF Pro Icons","Apple Legacy Chevron","PingFang SC","Helvetica Neue","Helvetica","Arial",sans-serif;
  }
</style>
