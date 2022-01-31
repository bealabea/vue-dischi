<template>
  <div>
    <div class="box text-center p-3 m-3">
        <img class="img-fluid pb-3" :src="disc.poster" alt="">
        <h5 class="text-uppercase">{{disc.title}}</h5>
        <div class="pt-2 disc-info">{{disc.author}}</div>
        <div class="disc-info">{{disc.year}}</div>
    </div>
  </div>
</template>

<script>
export default {

  props: {
    disc: Object
  }
}
</script>

<style scoped lang="scss">
.box {
    width: 200px;
    height: 350px;
    background-color: #2e3a46;
    cursor: pointer;
    img {
        transform: scale(1.0);
        transition: transform .5s;
        &:hover {
            transform: scale(1.1);
        }
    }
    .disc-info {
        font-size: 18px;
        color: #9e9e9e;
    }
}
</style>