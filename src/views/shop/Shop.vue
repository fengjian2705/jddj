<template>
<div class="wrapper">
  <div class="search">
    <div class="search__back iconfont" @click="handleBackClick">&#xe600;</div>
    <div class="search__content">
     <span class="search__content__icon iconfont">&#xe65c;</span>
     <input class="search__content__input" placeholder="请输入商品名称搜索"/>
    </div>
   </div>
   <ShopInfo :item="item" :hideBorder="true" :v-show="item.imgUrl"/>
</div>
</template>
<script>
import { reactive, toRefs } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import { get } from '../../utils/request'
import ShopInfo from '../../components/ShopInfo.vue'

// 获取当前商铺信息
const useShopInfoEffect = () => {
  const route = useRoute()
  const data = reactive({ item: {} })
  const getItemData = async () => {
    const result = await get(`/api/shop/${route.params.id}`)
    if (result?.errno === 0 && result?.data) {
      data.item = result.data
    }
  }
  const item = toRefs(data)
  return { item, getItemData }
}

const useBackRouterEffect = () => {
  const router = useRouter()
  const handleBackClick = () => {
    router.back()
  }
  return { handleBackClick }
}

export default {
  name: 'Shop',
  components: {
    ShopInfo
  },
  setup () {
    const { item, getItemData } = useShopInfoEffect()
    const { handleBackClick } = useBackRouterEffect()
    getItemData()
    return { item, handleBackClick }
  }
}
</script>
<style lang="scss" scoped>
@import "../../styles/virables.scss";

.wrapper{
    padding: 0 .18rem;
}
.search{
    margin: .2rem 0 .04rem 0;
    display: flex;
    line-height: .32rem;
    &__back{
        width: .3rem;
        font-size: .24rem;
        color: #b6b6b6;
    }
    &__content{
        display: flex;
        flex: 1;
        background: $search-bg-color;
        border-radius: .16rem;
        &__icon{
            width: .44rem;
            text-align: center;
            color: $search-font-color;
        }
        &__input{
            display: block;
            width: 100%;
            padding-right: .2rem;
            border: none;
            outline: none;
            background: none;
            height: .32rem;
            font-size: .14rem;
            color: $content-font-color;
            &::placeholder{
                color: $content-font-color;
                }
        }
    }
}
</style>
