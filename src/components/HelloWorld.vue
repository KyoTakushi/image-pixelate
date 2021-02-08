<template>
  <div class="global-wrapper">
    <MainCanvas />
  </div>
</template>

<script>
import MainCanvas from "./MainCanvas"

export default {
  name: 'HelloWorld',
  components: {
    MainCanvas
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.global-wrapper {
  //background: #000;
}
</style>