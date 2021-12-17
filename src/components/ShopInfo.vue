<template>
  <div class="shop__item">
    <img :src="item.imgUrl" class="shop__item__img"/>
    <div class="shop__content" :class="{'shop__content': true, 'shop__content--bordered': hideBorder ? false : true }">
    <div class="shop__content__title">{{item.name}}</div>
    <div class="shop__content_tags">
    <span class="shop__content__tag">月售：{{item.sales}}</span>
    <span class="shop__content__tag">起送：{{item.experssLimig}}</span>
    <span class="shop__content__tag">基础运费：{{item.expressPrice}}</span>
    </div>
    <div class="shop__content__highlight">
      {{item.slogan}}
    </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ShopInfo',
  props: [
    'item',
    'hideBorder'
  ],
  setup (props, context) {
  }
}
</script>
<style lang="scss" scoped>
@import "../styles/virables.scss";
 .shop__item {
    display: flex;
    padding-top: 0.12rem;
    &__img {
      margin-right: 0.16rem;
      width: 0.56rem;
      height: 0.56rem;
    }
  }
.shop__content {
  flex: 1;
  padding-bottom: 0.12rem;
  &__title {
    line-height: 0.22rem;
    font-size: 0.16rem;
    color: $content-font-color;
  }
  &__tags {
    margin-top: 0.08rem;
    line-height: 0.18rem;
    font-size: 0.13rem;
    color: $content-font-color;
  }
  &__tag {
    margin-right: 0.16rem;
  }
  &__highlight {
    margin: 0.08rem 0 0 0;
    line-height: 0.18rem;
    font-size: 0.13rem;
    color: #e93b3b;
  }
}
 .shop__content--bordered{
    border-bottom: 0.01rem solid $content-bg-color;
  }
</style>
