<template>
  <div>
    <header class="p-3">
      <img  src="@/assets/spotify-logo.png" alt="">
    </header>
    <loader-app v-if="discLoad"/>
    <div class="disc-container d-flex flex-wrap py-5">
      <disc-box v-for="(disc, index) in discList"
      :key="index"
      :disc="disc"/>
    </div>
  </div>
</template>

<script>
import DiscBox from './DiscBox.vue'
import LoaderApp from './LoaderApp.vue'
export default {
  components: {
    DiscBox,
    LoaderApp
  },
  props: {
    discList: Array,
    discLoad: Boolean
  }
}
</script>

<style scoped lang="scss">
@import '@/style/loader.scss';
header {
  background-color: #2e3a46;
  img {
    width: 40px;
  }
}
.disc-container {
  width: 1200px;
  margin: 0 auto;
}
</style>

