<script setup>
const pokemon = defineProps(["name", "url"]);

const pokemonId = pokemon.url.split("/")[6].toString().padStart(3, "0");
</script>

<template>
  <div class="pokemon col-4 text-capitalize">
    <div class="card mb-1 shadow">
      <img
        class="card-img-top"
        :src="
          'https://assets.pokemon.com/assets/cms2/img/pokedex/detail/' +
          pokemonId +
          '.png'
        "
        :alt="pokemon.name"
      />
      <div class="card-body">
        <h5 class="card-title">{{ pokemon.name }}</h5>
      </div>
    </div>
  </div>
</template>

<style>
.pokemon {
  margin-bottom: 5px;
}
.shadow {
  box-shadow: 0 20px rgba(0, 0, 0, 0.15);
  text-align: center;
}

.card-title {
  font-weight: 600;
}
</style>
