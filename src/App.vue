<script>
  import { store } from "./store";
  import axios from "axios";
  import AppHeader from '/src/components/AppHeader.vue';
  import AppSearch from '/src/components/AppSearch.vue';

  export default {
    components: {
      AppHeader,
      AppSearch,
    },
    data() {
      return {
        store,
        // array: []
      }
    },
    created() {
      axios
        .get("https://rickandmortyapi.com/api/character")
        .then((resp) => {
          this.store.cardsList = resp.data.results;
          // this.array = resp.data.results;
          // console.log(this.array);
        })
    },
    methods: {
      getCards() {
        console.log("Get cards", this.store.selectedStatus);
        axios.get("https://rickandmortyapi.com/api/character", {
          params: {
            status: this.store.selectedStatus,
          }
        }).then((resp) => {
          this.store.cardsList = resp.data.results;
        })
      }
    },
  }
</script>

<template>
  <AppHeader />
  <AppSearch @filter="getCards" />

  <!-- :array="array" -->

  <div class="container">
    <div class="grid" v-for="item in store.cardsList">
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