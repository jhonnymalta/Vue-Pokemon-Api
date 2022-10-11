<template>
  <div>
    <h3>Pokemon: {{ $route.params.name }}</h3>
    <img :src="poke.sprites?.front_default" alt="imagem pokemon" />
    <h2></h2>
    <div>
      <button @click="back">Voltar</button>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();

const poke = ref({});

const getData = async () => {
  try {
    const { data } = await axios.get(
      `https://pokeapi.co/api/v2/pokemon/${route.params.name}`
    );
    poke.value = data;
  } catch (error) {
    console.log(error);
  }
};

const back = () => {
  router.push("/pokemon");
};

getData();
</script>

<style lang="scss" scoped></style>
