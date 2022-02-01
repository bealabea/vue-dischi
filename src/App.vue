<template>
  <div id="app">
    <disc-list :discList="discList" :discLoad="discLoad"/>
  </div>
</template>

<script>
import DiscList from './components/DiscList.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    DiscList
  },
  data(){
    return {
      discList: [],
      discLoad: true,
    }
  },
  mounted(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((response) => {
      this.discList = response.data.response;
      this.discLoad = false;
    })
  }
}
</script>

<style lang="scss">
@import './style/main.scss'
</style>
