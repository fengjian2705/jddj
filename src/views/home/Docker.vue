<template>
  <div class="docker">
    <div
        v-for="(item,index) in dockerList"
        :key="index"
        :class="{'docker__item':true, 'docker__item--active':index==0}">
      <div class="iconfont" v-html="item.icon"/>
      <div class="docker__title">{{item.text}}</div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Docker',
  setup () {
    const dockerList = [
      { icon: '&#xe7c6;', text: '首页' },
      { icon: '&#xe638;', text: '购物车' },
      { icon: '&#xe60c;', text: '订单' },
      { icon: '&#xe610;', text: '我的' }
    ]
    return {
      dockerList
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../styles/virables.scss";
@import "../../styles/mixins.scss";
.docker {
  display: flex;
  position: absolute;
  box-sizing: border-box;
  padding: 0 0.18rem;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 0.49rem;
  border-top: 0.01rem solid $content-bg-color;
  color: $content-font-color;
  &__item {
    flex: 1;
    text-align: center;
    .iconfont {
      margin: 0.07rem 0 0.02rem 0;
      font-size: 0.18rem;
    }
    &--active {
      color: #2c29d6;
    }
  }
  &__title {
    font-size: 0.2rem;
    transform: scale(0.5, 0.5);
    transform-origin: center top;
  }
}
</style>
