<template>
  <div>
    <h1>Pokemon Vue</h1>
    <div>
      <ul>
        <li v-for="poke in Pokemons" :key="poke.name">
          <router-link :to="`/pokemon/${poke.name}`">{{
            poke.name
          }}</router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";
import { RouterLink } from "vue-router";

const Pokemons = ref([]);

const getData = async () => {
  try {
    const { data } = await axios.get("https://pokeapi.co/api/v2/pokemon");
    Pokemons.value = data.results;
  } catch (error) {
    console.log(error);
  }
};

getData();
</script>

<style lang="scss" scoped></style>
