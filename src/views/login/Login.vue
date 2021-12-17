<template>
  <div class="wrapper">
    <img
      class="wrapper__img"
      src="http://www.dell-lee.com/imgs/vue3/user.png"
      alt=""
    />
    <div class="wrapper__input">
      <input
        class="wrapper__input__content"
        placeholder="请输入手机号"
        v-model="username"
        autocomplete="false"/>
    </div>
    <div class="wrapper__input">
      <input
        class="wrapper__input__content"
        placeholder="请输入密码"
        type="password"
        v-model="password"
        autocomplete="false"/>

    </div>
    <div class="wrapper__login-button" @click="handleLogin">登录</div>
    <div class="wrapper__login-link" @click="hanldeRegisterClick">立即注册</div>
    <Toast v-if="show" :message="message"/>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'
import { useRouter } from 'vue-router'
import { post } from '../../utils/request'
import Toast, { useToastEffect } from '../../components/Toast'

const useLoginEffect = (showToast) => {
  const router = useRouter()
  const data = reactive({ username: '', password: '' })
  const handleLogin = async () => {
    try {
      const result = await post('/api/user/login', {
        username: data.username,
        password: data.password
      })
      if (result?.errno === 0) {
        localStorage.isLogin = true
        router.push({ name: 'Home' })
      } else {
        showToast('登陆失败')
      }
    } catch (error) {
      showToast('请求失败')
    }
  }
  const { username, password } = toRefs(data)
  return { handleLogin, username, password }
}
const useRegisterEffect = () => {
  const router = useRouter()
  const hanldeRegisterClick = () => {
    router.push({ name: 'Register' })
  }
  return { hanldeRegisterClick }
}
export default {
  name: 'Login',
  components: {
    Toast
  },
  // 代码的执行逻辑
  setup () {
    const { show, message, showToast } = useToastEffect()
    const { username, password, handleLogin } = useLoginEffect(showToast)
    const { hanldeRegisterClick } = useRegisterEffect()
    return { show, message, username, password, handleLogin, hanldeRegisterClick }
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
    &__login-button{
        margin: .32rem .4rem .16rem .4rem;
        line-height: .48rem;
        font-size: .16rem;
        text-align: center;
        background:#0091ff ;
        box-shadow: 0 .04rem .08rem 0 rgba(0,145,255,0.32);
        border-radius: .04rem;
        color: #fff;
    }

    &__login-link{
        font-size: .14rem;
        color: $content-notice-font-color;
        text-align: center;
    }
}
</style>
