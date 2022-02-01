<template>
  <div id="app">
    <header class="p-3 d-flex justify-content-between">
      <img src="@/assets/spotify-logo.png" alt="" />
      <select-app @search="filterResult" />
    </header>
    <disc-list :discList="genreList" :discLoad="discLoad" />
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
      genreList: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.discList = response.data.response;
        this.genreList = response.data.response;
        this.discLoad = false;
      });
  },
  methods: {
    filterResult(genreSelection) {
      if (genreSelection === "all") {
        this.genreList = this.discList;
      } else {
        this.genreList = this.discList.filter((disc) => {
          return disc.genre.toLowerCase().includes(genreSelection);
        });
      }
    },
  },
};
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
