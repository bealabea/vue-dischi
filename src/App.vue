<template>
  <div id="app">
    <disc-list :discList="discList"/>
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
      discList: []
    }
  },
  mounted(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((response) => {
      this.discList = response.data.response
    })
  }
}
</script>

<style lang="scss">
@import './style/main.scss'
</style>
