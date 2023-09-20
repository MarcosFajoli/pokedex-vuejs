<script setup>
import { onMounted, reactive, ref } from "vue";
import ListPokemons from "../components/ListPokemons.vue";
import ShowPokemon from "../components/ShowPokemon.vue";
import defaultPokemon from "../utils/defaultPokemon.json";

let pokemons = reactive(ref());
let selectedPokemon = reactive({
  value: defaultPokemon,
});

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon/?limit=20&offset=0")
    .then((response) => response.json())
    .then((response) => {
      pokemons.value = response.results;
      console.log(response);
    });
});

async function showPokemon(pokemon) {
  const response = await fetch(pokemon.url);
  selectedPokemon.value = await response.json();
  console.log(selectedPokemon.value);
}
</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div
          id="pokemon"
          class="col-sm-12 col-md-6 d-flex justify-content-center sticky"
        >
          <ShowPokemon
            :key="selectedPokemon.value.name"
            :value="selectedPokemon.value"
          />
        </div>
        <div class="col-sm-12 col-md-6 mb-5">
          <div class="card">
            <div class="card-body row">
              <ListPokemons
                v-for="pokemon in pokemons"
                :key="pokemon.name"
                :name="pokemon.name"
                :url="pokemon.url"
                @click="showPokemon(pokemon)"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style>
#pokemon {
  height: 80vh;
}
.sticky {
  position: -webkit-sticky; /* Para compatibilidade com navegadores mais antigos */
  position: sticky;
  top: 10vh;
}

.card {
  border: 0;
}
</style>
