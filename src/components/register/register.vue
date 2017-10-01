<template>
  <transition name="modal">
    <div class="register-wrap">
      <div class="register-body">
        <div class="register-header">
          <div class="t1">申请成为</div>
          <div class="t2">极果优品供应商</div>
        </div>
        <div class="register-input-box">
          <div class="register-input-body">
            <div class="register-item-wrap">
              <div class="register-item-text">产品名称：</div>
              <div class="register-item-input">
                <input type="text" name=""/>
              </div>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text">产品特点：</div>
              <div class="register-item-input">
                <textarea name=""></textarea>
              </div>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text">厂商全称：</div>
              <div class="register-item-input">
                <input type="text" name=""/>
              </div>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text">官方网站：</div>
              <div class="register-item-input">
                <input type="text" name=""/>
              </div>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text">电商网址：</div>
              <div class="register-item-input">
                <input type="text" name=""/>
              </div>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text"><span class="g2">*</span>联系人：</div>
              <div class="register-item-input">
                <input type="text" name=""/>
              </div>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text"><span class="g2">*</span>手机号：</div>
              <div class="register-item-input">
                <input type="text" name=""/>
              </div>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text"><span class="g2">*</span>微信号：</div>
              <div class="register-item-input">
                <input type="text" name=""/>
              </div>
            </div>
          </div>

          <div class="register-item-wrap">
            <div class="register-item-text"></div>
            <div class="register-submit-wrap">
              <button type="button" >提交</button>
            </div>
          </div>

        </div>
        <div class="register-close" @click="close">
          <img src="../../style/images/close.svg"/>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'register',
    data () {
      return {
      }
    },
    methods: {
      close () {
        this.$emit('close')
      }
    }
  }
</script>

<style lang="less" rel="stylesheet/less" scoped>
  input, textarea, button {
    appearance: none;
    resize: none;
  }

  .register-wrap {
    line-height: 33px;
    background-color: rgba(255, 255, 255, 0.8);
    position: fixed;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    z-index: 9;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all .3s ease;
    .register-body {
      width: 100%;
      background: #FCF9F2;
      box-shadow: 0 5px 14px 0 rgba(0, 0, 0, 0.20);
      position: relative;
    }
  }

  .register-header {
    text-align: center;
    background-color: #fff;
    line-height: 33px;
    padding: 25px 0;
    .t1 {
      color: #6C4607;
      font-size: 24px;
    }
    .t2 {
      color: #6C4607;
      font-size: 24px;
      font-weight: bold;
    }
  }

  .register-input-box {
    padding: 45px;
    .register-item-wrap {
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
      align-items: stretch;
      margin: 18px 0;
      border-radius: 5px;
      overflow: hidden;
    }
    .register-item-text {
      color: #6C4607;
      font-size: 24px;
      font-weight: 500;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-content: center;
      align-items: center;
      width: 120px;
      .g2 {
        color: #F66039;
      }
    }
    .register-item-input {
      background-color: #E7DFCC;
      flex: 1;
      padding: 12px 20px;
      input, textarea {
        outline: none;
        border: none;
        background-color: transparent;
        display: block;
        width: 100%;
        line-height: 33px;
        font-size: 24px;
      }
      textarea {
        height: 150px;
      }
    }
    .register-submit-wrap {
      background-color: #E7DFCC;
      &.on{
        background-color: #F66039;
      }
      button[type=button] {
        padding: 12px 20px;
        color: #fff;
        font-size: 24px;
        background-color: transparent;
        width: 230px;
        border: none;
        outline: none;
      }
    }
  }

  .register-close {
    background: #FFFFFF;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.30);
    width: 80px;
    height: 80px;
    border-radius: 50%;
    overflow: hidden;
    position: absolute;
    left: 50%;
    transform: translateY(30px) translateX(-50%);
    display: flex;
    justify-content: center;
    align-items: center;
    img {
      width: 30px;
    }
  }

  .modal-enter {
    opacity: 0;
  }

  .modal-leave-active {
    opacity: 0;
  }

  .modal-enter,
  .modal-leave-active {
    -webkit-transform: scale(1.1);
    transform: scale(1.1);
  }
</style>
