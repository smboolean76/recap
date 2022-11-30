<script>
import { store } from "./store";
import axios from "axios";

import HelloWorld from "./components/HelloWorld.vue";
export default {
  components: {
    HelloWorld,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    saluta(data) {
      console.log(data);
    },
  },
  created() {
    axios.get("https://pokeapi.co/api/v2/pokemon").then((res) => {
      this.store.pokemon = res.data.results;
    });

    axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "e99307154c6dfb0b4750f6603256716d",
          query: "ritorno",
          language: "it-IT",
        },
      })
      .then((res) => {
        this.store.movies = res.data.results;
      });
  },
};
</script>

<template>
  <div>
    <h2 style="color: red" v-if="store.text === 'franco'">{{ store.text }}</h2>
    <HelloWorld @cliccato="saluta" msg="Hello World" />
  </div>
</template>

<style lang="scss">
@import "./style/global.scss";
</style>
