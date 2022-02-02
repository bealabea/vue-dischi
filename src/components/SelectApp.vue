<template>
    <div class="text-center">
        <label for="genre" class="px-3">FILTRA PER GENERE</label>
        <select name="genre" id="genre" v-model="selected" @change="$emit('selection', selected)">
            <option value="all">All</option>
            <option v-for="(disc, index) in genreList" :key="index" :value="disc.genre">{{disc.genre}}</option> 
        </select>   
    </div>
</template>

<script>
export default {
    props: {
    discList: Array,
    filteredList: Array,
    genreList: Array,
  },
  data() {
    return {
      selected:'all'
    }
  }
}
</script>

<style scoped lang="scss">
</style>