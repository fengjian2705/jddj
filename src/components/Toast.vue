<template>
    <div class="toast">{{message}}</div>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  name: 'Toast',
  props: ['message']
}
export const useToastEffect = () => {
  const toastData = reactive({
    show: false,
    message: ''
  })
  const showToast = (toastMessage) => {
    toastData.show = true
    toastData.message = toastMessage
    setTimeout(() => {
      toastData.show = false
      toastData.message = ''
    }, 2000)
  }
  const { show, message } = toRefs(toastData)
  return { showToast, show, message }
}
</script>

<style lang="scss" scoped>
    .toast {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        padding: .1rem;
        background: rgba(0, 0, 0, 0.35);
        border-radius: .05rem;
        color: #fff;
    }
</style>
