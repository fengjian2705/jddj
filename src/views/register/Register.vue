<template>
  <div class="wrapper">
    <img
      class="wrapper__img"
      src="http://www.dell-lee.com/imgs/vue3/user.png"
      alt=""
    />
    <div class="wrapper__input">
      <input class="wrapper__input__content" placeholder="请输入手机号" />
    </div>
    <div class="wrapper__input">
      <input class="wrapper__input__content" placeholder="请输入密码" type="password"/>

    </div>
    <div class="wrapper__input">
      <input class="wrapper__input__content" placeholder="确认密码" type="password"/>

    </div>
    <div class="wrapper__register-button" @click="handleRegister">立即注册</div>
    <div class="wrapper__register-link" @click="henldeLoginClick">已有账号去登陆</div>
  </div>
</template>

<script>
import { useRouter } from 'vue-router'

export default {
  name: 'Register',
  setup () {
    const router = useRouter()

    const henldeLoginClick = () => {
      router.push({ name: 'Login' })
    }
    return {
      henldeLoginClick
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../styles/virables.scss";

.wrapper{
    position: absolute;
    top: 50%;
    left: 0;
    right: 0;
    transform: translateY(-50%);
    &__img{
        display: block;
        width: .66rem;
        height: .66rem;
        margin: 0 auto .4rem;
    }
     &__input{
        background:#f9f9f9;
        height: .48rem;
        margin: 0 .4rem .16rem .4rem;
        padding: 0 .16rem;
        border: 1px solid rgba(0,0,0,0.1);
        border-radius: .06rem;
        &__content{
            line-height: .48rem;
            padding: 0;
            border: none;
            outline: none;
            background: none;
            width: 100%;
            font-size: .16rem;
            color: $content-notice-font-color;
            &::placeholder{
                color: $content-notice-font-color;
            }
        }
    }
    &__register-button{
        margin: .32rem .4rem .16rem .4rem;
        line-height: .48rem;
        font-size: .16rem;
        text-align: center;
        background:#0091ff ;
        box-shadow: 0 .04rem .08rem 0 rgba(0,145,255,0.32);
        border-radius: .04rem;
        color: #fff;
    }

    &__register-link{
        font-size: .14rem;
        color: $content-notice-font-color;
        text-align: center;
    }
}
</style>
