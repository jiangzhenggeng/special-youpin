<template>
  <div>
    <header-bg/>
    <register
      v-if="show_register"
      @close="closeRegister"
      :type="type"
      class="register"
    />
    <sub-header @openRegister="openRegister"/>
    <div class="classic-case">
      <div style="margin-bottom: 50px">
        <sub-header-item :sub_data="has_sub_item" :button="false"/>
      </div>
      <template v-for="i in [1,2,3,4,5]">
        <center-item />
      </template>
    </div>
    <footer-bottom />
  </div>
</template>

<script>
  import Register from './register/register.vue'
  import HeaderBg from './header-bg.vue'
  import FooterBottom from './footer.vue'
  import CenterItem from './center-item.vue'
  import SubHeader from './subheader/index.vue'
  import SubHeaderItem from './subheader/sub-header.vue'

  export default {
    data () {
      return {
        type:1,
        show_register: false,
        has_sub_item: {
          sub_logo: 'icon-11.png',
          sub_title: '经典案例',
          sub_en_title: 'Classic Case'
        }
      }
    },
    components: {
      Register,
      HeaderBg,
      SubHeader,
      SubHeaderItem,
      FooterBottom,
      CenterItem
    },
    methods: {
      openRegister (type) {
        this.show_register = true;
//        ['mousewheel','DOMMouseScroll','touchmove'].forEach((item)=>{
//          window.addEventListener(item,this._preventDefault, {passive: false });
//        });
        this.type = type || this.type;
      },
      closeRegister () {
        this.show_register = false;
//        ['mousewheel','DOMMouseScroll','touchmove'].forEach((item)=>{
//          window.removeEventListener(item,this._preventDefault);
//        });
      },
      _preventDefault(e){
        e.preventDefault();
        e.stopPropagation();
        return false;
      }
    }
  }
</script>

<style lang="less" rel="stylesheet/less">
  .classic-case {
    background: #fff;
    padding: 75px;
  }
</style>
