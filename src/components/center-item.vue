<template>
  <div class="item-wrap">
    <div class="item-img">
      <img src="../style/images/icon/img-1.jpg" />
    </div>
    <div class="item-title">
      <div class="n1">惠普战66轻薄笔记本</div>
      <div class="n2">攻城狮生产力的倍增器，惠普战66轻薄笔记本深度体验</div>
    </div>
  </div>
</template>

<style lang="less" rel="stylesheet/less">
  .item-wrap {
    margin: auto;
    margin-top: 10px;
    position: relative;
  }
  .item-img{
    background: rgba(0,0,0,0.60);
    border-radius: 4px;
    width: 600px;
    height: 300px;
    overflow: hidden;
    img{width: 100%;height: 100%}
  }
  .item-title{
    position: absolute;
    left: 0;
    bottom: 20px;
    width: 100%;
    text-align: center;
    color: #fff;
    .n1{
      line-height: 40px;
      font-size: 28px;
    }
    .n2{
      line-height: 28px;
      font-size: 20px;
      margin-top: 10px;
    }
  }
</style>
