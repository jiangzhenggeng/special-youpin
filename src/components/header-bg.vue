<template>
  <header class="header-icon-bg">
    <div class="header-logo">
      <img src="../style/images/icon/header-logo.png" />
    </div>
    <div class="header-text">
      <p>专业「内容电商」服务平台</p>
      <p>为用户甄选每一件商品</p>
      <p>用心服务千万优质商家、内容创业者</p>
    </div>
    <div class="header-youzan">
      <img src="../style/images/icon/header-youzan.png" />
      <span>有赞官方推荐优质分销商</span>
    </div>
  </header>
</template>

<script>
  export default {
    data () {
      return {}
    }
  }
</script>

<style lang="less" rel="stylesheet/less" scoped>
  .header-icon-bg{
    @h : 610px;
    height: @h;
    background-image: url(../style/images/icon/header-bg.jpg);
    background-repeat: no-repeat;
    background-size: auto @h;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    line-height: 32px;
    font-size: 22px;
    color: #fff;
  }
  .header-logo{
    margin-top: 150px;
    height: 85px;
    img{ height: 100% }
  }
  .header-text{
    margin-top: 80px;
  }
  .header-youzan{
    background: #FFFFFF;
    border-radius: 50px;
    line-height: 44px;
    color: #000;
    font-size: 14px;
    margin-top: 30px;
    padding:  0 35px;
    img{width: 20px}
  }
</style>
