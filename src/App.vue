<script>
  import axios from "axios";
  import AppHeader from '/src/components/AppHeader.vue';
  import AppMain from '/src/components/AppMain.vue';

  export default {
    components: {
      AppHeader,
      AppMain,
    },
    data() {
      return {
        array: []
      }
    },
    created() {
      axios
        .get("https://rickandmortyapi.com/api/character")
        .then((resp) => {
          this.array = resp.data.results
          console.log(this.array);
        })
    }
  }
</script>

<template>
  <AppHeader />
  <AppMain :array="array" />

  <div class="container">
    <div class="grid" v-for="item in array">
      <img :src="item.image" alt="">
      <h3>{{ item.name }}</h3>
      <span>{{ item.status }}</span> <br>
      <span>{{ item.species }}</span>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin: 0 100px;

    .grid {
      text-align: center;
      width: calc(100% / 4 - 20px);
    }

    img {
      border-radius: 50%;
      width: 200px;
    }

    h3 {
      padding-bottom: 10px;
    }
  }
</style>