<template>
    <div class="text-center">
        <label for="genre" class="px-3">FILTRA PER GENERE</label>
        <select name="genre" id="genre" v-model="selected" @change="$emit('search', selected)">
            <option value="all">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>   
    </div>
</template>

<script>
export default {
    props: {
    discList: Array,
    genreList: Array
  },
  data() {
    return {
      selected:''
    }
  }
}
</script>

<style scoped lang="scss">
</style>