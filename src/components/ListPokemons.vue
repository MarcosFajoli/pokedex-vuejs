<script setup>
const pokemon = defineProps(["name", "url"])

const pokemonId = pokemon.url.split("/")[6].toString().padStart(3, '0');

</script>

<template>
    <div class="col-4 text-capitalize">
        <div class="card mb-1">
            <img class="card-img-top" :src="'https://assets.pokemon.com/assets/cms2/img/pokedex/detail/' + pokemonId + '.png'" :alt="pokemon.name">
            <div class="card-body">
                <h5 class="card-title">{{ pokemon.name }}</h5>
                <a :href="pokemon.url" class="btn btn-primary">Ver Pokémon</a>
            </div>
        </div>
    </div>
</template>

<style>

</style>