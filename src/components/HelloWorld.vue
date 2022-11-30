<script>
import { store } from "../store";

export default {
  name: "HelloWord",
  props: {
    msg: String,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div>
    <h1>{{ msg }}</h1>
    <button @click="$emit('cliccato', 'Buongiorno')">Cliccami</button>
    <select v-model="store.text">
      <option value="">Seleziona un nome</option>
      <option value="franco">Franco</option>
      <option value="antonio">Antonio</option>
    </select>

    <ul>
      <li v-for="poke in store.pokemon">{{ poke.name }}</li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
h1 {
  @include media-breakpoint-up(md) {
    color: green;
  }
}
</style>
