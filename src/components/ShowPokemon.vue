<script setup>
const pokemon = defineProps({
  value: {
    id: Number,
    name: String,
    sprites: {
      other: {
        dream_world: {
          front_default: String,
        },
      },
    },
  },
});

const pokemonSrc = pokemon.value.sprites.other.dream_world.front_default;
</script>

<template>
  <div class="card" style="width: 28rem">
    <img
      class="card-img-top"
      :src="pokemonSrc"
      alt="Card image cap"
      style="max-height: 65vh"
    />
    <div class="card-body">
      <h5 class="card-title text-capitalize">{{ pokemon.value.name }}</h5>
      <p class="card-text">
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </p>
    </div>
  </div>
</template>

<style></style>
