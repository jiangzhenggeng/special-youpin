<template>
  <transition name="modal">
    <div class="register-wrap">
      <div style="width: 100%">
        <div class="register-body">
          <div class="register-header">
            <div class="t1">申请成为</div>
            <div class="t2">极果优品供应商</div>
          </div>
          <div class="register-input-box">
            <div class="register-input-body">
              <form ref="form-data">
                <template v-if="type==1">
                  <div class="register-item-wrap">
                    <div class="register-item-text">产品名称：</div>
                    <div class="register-item-input">
                      <input type="text" ref="v_pname" name="pname"/>
                      <div class="error-msg">填写产品名称</div>
                    </div>
                  </div>

                  <div class="register-item-wrap">
                    <div class="register-item-text">产品特点：</div>
                    <div class="register-item-input">
                      <textarea ref="v_feature" name="feature"></textarea>
                      <div class="error-msg">填写产品特点</div>
                    </div>
                  </div>

                  <div class="register-item-wrap">
                    <div class="register-item-text">厂商全称：</div>
                    <div class="register-item-input">
                      <input ref="v_factory_name" type="text" name="factory_name"/>
                      <div class="error-msg">填写厂商全称</div>
                    </div>
                  </div>

                  <div class="register-item-wrap">
                    <div class="register-item-text">官方网站：</div>
                    <div class="register-item-input">
                      <input ref="v_url" type="text" name="url"/>
                      <div class="error-msg">填写官方网站</div>
                    </div>
                  </div>

                  <div class="register-item-wrap">
                    <div class="register-item-text">电商网址：</div>
                    <div class="register-item-input">
                      <input ref="v_shop_url" type="text" name="shop_url"/>
                      <div class="error-msg">填写电商网址</div>
                    </div>
                  </div>
                </template>
                <template v-else-if="type==2">
                  <div class="register-item-wrap">
                    <div class="register-item-text">渠道性质：</div>
                    <div class="register-item-input radio">
                      <label><input type="radio" name="type" value="1" checked/>个人</label>
                      <label><input type="radio" name="type" value="2"/>公司</label>
                    </div>
                  </div>
                  <div class="register-item-wrap">
                    <div class="register-item-text"><span class="g2">*</span>渠道名称：</div>
                    <div class="register-item-input">
                      <input ref="v_name" type="text" name="name"/>
                      <div class="error-msg">填写渠道名称</div>
                    </div>
                  </div>
                  <div class="register-item-wrap">
                    <div class="register-item-text">渠道特点：</div>
                    <div class="register-item-input">
                      <textarea ref="v_feature" name="feature"></textarea>
                    </div>
                  </div>
                </template>

                <div class="register-item-wrap">
                  <div class="register-item-text"><span class="g2">*</span>联系人：</div>
                  <div class="register-item-input">
                    <input ref="v_username" type="text" name="username"/>
                    <div class="error-msg">填写联系人</div>
                  </div>
                </div>

                <div class="register-item-wrap">
                  <div class="register-item-text"><span class="g2">*</span>手机号：</div>
                  <div class="register-item-input">
                    <input ref="v_tel" type="text" name="tel"/>
                    <div class="error-msg">填写手机号</div>
                  </div>
                </div>

                <div class="register-item-wrap">
                  <div class="register-item-text"><span class="g2">*</span>微信号：</div>
                  <div class="register-item-input">
                    <input ref="v_weixin" type="text" name="weixin"/>
                    <div class="error-msg">填写微信号</div>
                  </div>
                </div>
              </form>
            </div>

            <div class="register-item-wrap">
              <div class="register-item-text"></div>
              <div class="register-submit-wrap" :class="{on}" @click="submitData">
                <button type="button">提交</button>
              </div>
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
  import $ from 'jquery'

  export default {
    name: 'register',
    props: {
      type: {
        type: Number,
        default: 1
      }
    },
    data () {
      return {
        on: false
      }
    },
    watch: {
      type () {
        $('.error-msg').hide()
      }
    },
    mounted () {
      var formFunction = this.getFormFunction()
      var _this = this
      $('.register-wrap').on('keyup change blur focus', 'input,textarea', function (e) {
        if(e.type=='focus'){
          $(window).scrollTop( $(this).offset().top - 10 );
        }
        _this.timer && clearTimeout( _this.timer );
        _this.timer = setTimeout(()=>{
          if ($(this).attr('name')) {
            var i = 'v_' + $(this).attr('name');
            if (formFunction[i] && _this.$refs[i] && i.substr(0, 2) == 'v_') {
              if (! formFunction[i].call(_this, _this.$refs[i]) ) {
                $(_this.$refs[i]).next().show()
              } else {
                $(_this.$refs[i]).next().hide()
              }
            }
          }
        },300);
      })
    },
    methods: {
      close () {
        this.$emit('close')
      },
      verification () {
        var result
        var formFunction = this.getFormFunction()
        var validataResult = true
        for (var i in this.$refs) {
          if (formFunction[i] && this.$refs[i] && i.substr(0, 2) == 'v_') {
            result = formFunction[i].call(this, this.$refs[i])
            if (!result) {
              $(this.$refs[i]).next().show()
              validataResult = false
            } else {
              $(this.$refs[i]).next().hide()
            }
          }
        }
        return validataResult
      },
      submitData () {
        if (this.verification()) {
          var url = this.type == 1 ? '/api/html/PostSupplier' : '/api/html/PostChannel'
          var formData = $(this.$refs['form-data']).serialize()
          $.get(url, formData,  (repalyData) => {
            if( repalyData.resultCode==0){
              this.$toast('提交成功');
              this.close();
            }else{
              this.$toast('提交失败');
            }
          }, 'json');
        }
      },
      getFormFunction () {
        return {
          v_pname: function ($ref) {
            if ($($ref).val().replace(/^\s+|\s+$/g, '') == '') {
              return false
            }
            return true
          },
          v_feature: function ($ref) {
            if ($($ref).val().replace(/^\s+|\s+$/g, '') == '') {
              return false
            }
            return true
          },
          v_factory_name: function ($ref) {
            if ($($ref).val().replace(/^\s+|\s+$/g, '') == '') {
              return false
            }
            return true
          },
          v_url: function ($ref) {
            if (!/^https?\:\/\/.+/.test($($ref).val())) {
              return false
            }
            return true
          },
          v_shop_url: function ($ref) {
            if (!/^https?\:\/\/.+/.test($($ref).val())) {
              return false
            }
            return true
          },
          v_name: function ($ref) {
            if ($($ref).val().replace(/^\s+|\s+$/g, '') == '') {
              return false
            }
            return true
          },
          v_username: function ($ref) {
            if ($($ref).val().replace(/^\s+|\s+$/g, '').length < 2) {
              return false
            }
            return true
          },
          v_tel: function ($ref) {
            if (!/^1\d{10}$/.test($($ref).val())) {
              return false
            }
            return true
          },
          v_weixin: function ($ref) {
            if (!/^[\d\w\-]+$/.test($($ref).val())) {
              return false
            }
            return true
          }
        }
      }
    }
  }
</script>

<style lang="less" rel="stylesheet/less" scoped>
  input, textarea, button {
    appearance: none;
    resize: none;
  }

  input:-webkit-autofill {
    box-shadow: inset 0 0 0 1000px #E7DFCC;
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
    flex-direction: column;
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
      justify-content: flex-end;
      align-content: center;
      align-items: center;
      width: 135px;
      text-align: right;
      .g2 {
        color: #F66039;
      }
    }
    .register-item-input {
      background-color: #E7DFCC;
      flex: 1;
      padding: 12px 20px;
      position: relative;
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
      &.radio {
        background: transparent;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        padding-left: 0;
      }
    }
    .register-submit-wrap {
      user-select: none;
      background-color: #E7DFCC;
      &.on {
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
    position: relative;
    margin: 10px auto auto;
    /*transform: translateY(30px) translateX(-50%);*/
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

  .radio {
    label {
      position: relative;
      display: block;
      overflow: hidden;
      padding-left: 40px;
      margin-right: 10px;
    }
    input[type=radio] {
      position: absolute;
      left: 0;
      top: 50%;
      transform: translateY(-50%);

      &:after {
        content: '';
        display: block;
        width: 30px;
        height: 30px;
        background: #E7DFCC;
        border-radius: 7px;
      }

      &:checked:after {
        background-image: url(../../style/images/icon-radio.svg);
        background-position: center center;
        background-size: 16px auto;
        background-repeat: no-repeat;
      }
    }
  }

  .error-msg {
    position: absolute;
    right: 15px;
    top: 50%;
    transform: translateY(-50%);
    color: #F66039;
    font-size: 24px;
    display: none;
  }
</style>
