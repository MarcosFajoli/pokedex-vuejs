<script setup>
import typeColor from "../utils/typeColor";
import { onMounted } from "vue";

const pokemon = defineProps({
  value: Object,
});

const pokemonSrc = pokemon.value.sprites.other.dream_world.front_default;

onMounted(() => {
  document.getElementById("card-text").style.color =
    typeColor[pokemon.value.types[0].type.name];
});

console.log(pokemon.value.types[0].type.name);
</script>

<template>
  <div class="card" style="width: 28rem">
    <img
      class="card-img-top"
      :src="pokemonSrc"
      alt="Card image cap"
      style="max-height: 30vh"
    />
    <div class="card-body">
      <h5 class="card-title text-capitalize">{{ pokemon.value.name }}</h5>
      <p class="card-text" id="card-text">
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </p>
    </div>
  </div>
</template>

<style></style>
