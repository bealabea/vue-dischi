<template>
  <div id="app">
    <header class="p-3 d-flex justify-content-between">
      <img src="@/assets/spotify-logo.png" alt="" />
      <select-app @selection="filterResult" :genreList="genreList"/>
    </header>
    <disc-list :discList="filteredList" :discLoad="discLoad"/>
  </div>
</template>

<script>
import DiscList from "./components/DiscList.vue";
import axios from "axios";
import SelectApp from "./components/SelectApp.vue";

export default {
  name: "App",
  components: {
    DiscList,
    SelectApp,
  },
  data() {
    return {
      discList: [],
      discLoad: true,
      filteredList: [],
      genreList: []
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.discList = response.data.response;
        this.filteredList = response.data.response;
        this.discLoad = false;
        this.getGenreList();
      });
  },
  methods: {
    filterResult(genreSelection) {
      if (genreSelection === "all") {
        this.filteredList = this.discList;
      } else {
        this.filteredList = this.discList.filter((disc) => {
          return disc.genre.toLowerCase() === genreSelection.toLowerCase();
        });
      }
    },
    getGenreList(){
        this.genreList = this.discList.filter((disc)=> {
        if (!this.genreList.includes(disc.genre)){
        return this.genreList.push(disc.genre);
        }
      });
    }
  }
}
</script>

<style lang="scss">
@import "./style/main.scss";
header {
  background-color: #2e3a46;
  img {
    width: 40px;
  }
}
</style>
