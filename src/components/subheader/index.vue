<template>
  <div class="body-header-item">
    <div v-for="item in sub_item" class="sub-header-wrap">
      <sub-header
        :sub_data="item.sub_header"
        :item="item"
        @openRegister="openRegister"
      />
      <div class="sub-item-wrap">
        <sub-item
          v-for="item2 in item.sub_item"
          :item="item2"
        />
      </div>
    </div>
  </div>
</template>

<script>
  import SubHeader from './sub-header.vue'
  import SubItem from './sub-item.vue'

  export default {
    data () {
      return {
        sub_item: [
          {
            sub_header: {
              sub_logo: 'icon-1.png',
              sub_title: '招募供货商',
              sub_en_title: 'Recruit Suppliers',
              sub_desc: '好产品轻松找到目标消费者'
            },
            sub_item: [
              {
                icon: '2',
                title: '1亿+精准消费流量',
                desc: `<p>覆盖主流自媒体渠道</p><p>轻松找到目标消费者</p><p>全程无忧完成销售</p>`
              },
              {
                icon: '3',
                title: '8%微信爆文转化',
                desc: `<p>免费提供产品文案</p><p>专业内容包装高于业界转化率</p><p>最高达8%</p>`
              },
              {
                icon: '4',
                title: '有赞优质分销商',
                desc: `<p>完善的一站式分销服务解</p><p>决方案，轻松找到目标消费者购买</p><p>转化率、流量高于业界水平</p>`
              },
              {
                icon: '5',
                title: '品牌曝光',
                desc: `<p>全媒体平台资源提升品牌曝光度</p>`
              }
            ],
            type:1
          },
          {
            sub_header: {
              sub_logo: 'icon-6.png',
              sub_title: '招募分销商',
              sub_en_title: 'Recruit Distributor',
              sub_desc: '有渠道  有流量  轻松变现'
            },
            sub_item: [
              {
                icon: '7',
                title: '高分销利润',
                desc: `<p>一键完成分销  高额利润</p><p>VIP客服一对一指导服务</p>`
              },
              {
                icon: '8',
                title: '1000+品质好物',
                desc: `<p>家居、黑科技、户外、汽车周边<br>每天都有海内外爆品上新<br>提供高转化率微信爆文</p>`
              },
              {
                icon: '9',
                title: '品质保障',
                desc: `<p>100%正品保障，近乎0投诉<br>真正解决用户痛点<br>提升用户口碑</p>`
              },
              {
                icon: '10',
                title: '安心售后',
                desc: `<p>7x16小时专业售后在线<br>免除后顾之忧<br>库存充足24小时发货</p>`
              }
            ],
            type:2
          }
        ]
      }
    },
    components: {
      SubHeader,
      SubItem,
    },
    methods: {
      openRegister (type) {
        this.$emit('openRegister',type)
      }
    }
  }
</script>

<style lang="less" rel="stylesheet/less">
  .sub-header-wrap {
    text-align: center;
    padding: 75px 0;
    &:nth-child(odd) {
      background: #fff;
    }
  }

  .sub-item-wrap {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }
</style>
