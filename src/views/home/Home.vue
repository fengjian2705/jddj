<template>
  <div>
    <div class="wrapper">
      <StaticPart/>
      <Nearby/>
    </div>
    <Docker/>

  </div>
</template>
<script>
import StaticPart from './StaticPart.vue'
import Nearby from './Nearby.vue'
import Docker from './Docker.vue'

export default {
  name: 'Home',
  components: {
    StaticPart,
    Nearby,
    Docker
  }
}
</script>
<style lang="scss" scoped>
@import "../../styles/virables.scss";
@import "../../styles/mixins.scss";
.wrapper {
  overflow-y: auto;
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0.5rem;
  padding: 0 0.18rem 0.1rem 0.18rem;
  width: 100%;
  box-sizing: border-box;
}
</style>
