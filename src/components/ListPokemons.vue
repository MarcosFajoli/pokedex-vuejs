<script setup>
const pokemon = defineProps(["name", "url"])

</script>

<template>
    <div class="col-4 text-capitalize">
        <div class="card mb-1">
            <img class="card-img-top" src="pokebola.png" :alt="pokemon.name">
            <div class="card-body">
                <h5 class="card-title">{{ pokemon.name }}</h5>
                <a :href="pokemon.url" class="btn btn-primary">Ver Pokémon</a>
            </div>
        </div>
    </div>
</template>

<style>

</style>