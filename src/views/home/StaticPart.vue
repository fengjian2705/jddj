<template>
  <div>
    <div class="position">
      <span class="iconfont position__icon">&#xe6a4;</span>
      北京理工大学国防科技园2号楼10层
      <span class="iconfont position__notice">&#xe69f;</span>
    </div>
    <div class="search">
      <span class="iconfont">&#xe65c;</span>
      山姆会员店优惠商品
    </div>
    <div class="banner">
      <img
        class="banner__img"
        src="http://www.dell-lee.com/imgs/vue3/banner.jpg"
      />
    </div>
    <div class="icons">
      <div class="icons__item" v-for="(item,index) in iconList" :key="index">
        <img
          class="icons__item__img"
          :src="`http://www.dell-lee.com/imgs/vue3/${item.imageName}.png`"
        />
        <p class="icons__item__desc">{{item.desc}}</p>
      </div>
    </div>
    <div class="gap"></div>
  </div>
</template>

<script>
export default {
  name: 'StaticPart',
  setup () {
    const iconList = [
      { imageName: '超市', desc: '超市便利' },
      { imageName: '菜市场', desc: '菜市场' },
      { imageName: '水果店', desc: '水果店' },
      { imageName: '鲜花', desc: '鲜花绿植' },
      { imageName: '医药健康', desc: '医药健康' },
      { imageName: '家居', desc: '家居时尚' },
      { imageName: '蛋糕', desc: '蛋糕烘焙' },
      { imageName: '签到', desc: '签到' },
      { imageName: '大牌免运', desc: '大牌免运' },
      { imageName: '红包', desc: '红包套餐' }
    ]
    return {
      iconList
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../../styles/virables.scss';
@import '../../styles/mixins.scss';
.position {
  position: relative;
  padding: 0.16rem 0.24rem 0.16rem 0;
  line-height: 0.22rem;
  font-size: 0.16rem;
  color: $content-font-color;
  @include ellipsis;
  .position__icon {
    position: relative;
    top: 0.01rem;
    font-size: 0.2rem;
  }
  .position__notice {
    position: absolute;
    right: 0;
    top: 0.17rem;
    font-size: 0.2rem;
  }
}

.search {
  margin-bottom: 0.12rem;
  line-height: 0.32rem;
  background: #f5f5f5;
  color: #b7b7b7;
  border-radius: 0.16rem;
  font-size: 0.14rem;
  .iconfont {
    position: relative;
    top: 0.02rem;
    font-size: 0.2rem;
    display: inline-block;
    padding: 0 0.12rem 0 0.16rem;
  }
}

.banner {
  height: 0;
  overflow: hidden;
  padding-bottom: 25.4%;
  &__img {
    width: 100%;
  }
}

.icons {
  display: flex;
  flex-wrap: wrap;
  margin-top: 0.16rem;
  &__item {
    width: 20%;
    &__img {
      display: block;
      width: 0.4rem;
      height: 0.4rem;
      margin: 0 auto;
    }
    &__desc {
      margin: 0.06rem 0 0.16rem 0;
      text-align: center;
      color: $content-font-color;
    }
  }
}

.gap {
  margin: 0 -0.18rem;
  height: 0.1rem;
  background: $content-bg-color;
}
</style>
