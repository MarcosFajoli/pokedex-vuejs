<script setup>
import typeColor from "../utils/typeColor";
import { onMounted } from "vue";

const pokemon = defineProps({
  value: Object,
});

const pokemonSrc = pokemon.value.sprites.other.dream_world.front_default;
const hp = pokemon.value.stats[0].base_stat;
const pokeName =
  pokemon.value.name[0].toUpperCase() + pokemon.value.name.slice(1);
const statAttack = pokemon.value.stats[1].base_stat;
const statDefense = pokemon.value.stats[2].base_stat;
const statSpeed = pokemon.value.stats[5].base_stat;
const weight = parseInt(pokemon.value.weight) / 10;
const height = parseInt(pokemon.value.height) / 10;

onMounted(() => {
  const card = document.getElementById("card");

  let appendTypes = (types) => {
    types.forEach((item) => {
      let span = document.createElement("SPAN");
      span.textContent = item.type.name;
      document.querySelector(".types").appendChild(span);
    });
  };

  let styleCard = (color) => {
    card.style.background = `radial-gradient(circle at 50% 0%, ${color} 36%, #ffffff 36%)`;
    card.querySelectorAll(".types span").forEach((type, key) => {
      type.style.backgroundColor =
        typeColor[pokemon.value.types[key].type.name];
      console.log(key);
    });
    card.querySelectorAll(".a span");
  };

  appendTypes(pokemon.value.types);
  styleCard(typeColor[pokemon.value.types[0].type.name]);
});
</script>

<template>
  <div id="card" style="width: 28rem">
    <p class="hp">
      <span>HP</span>
      {{ hp }}
    </p>
    <img :src="pokemonSrc" />
    <h2 class="poke-name">{{ pokeName }}</h2>
    <div class="types"></div>
    <div class="attributes">
      <div>
        <h3>{{ height }}m</h3>
        <p>Height</p>
      </div>
      <div>
        <h3>{{ weight }}kg</h3>
        <p>Weight</p>
      </div>
    </div>
    <div class="stats">
      <div>
        <h3>{{ statAttack }}</h3>
        <p>Attack</p>
      </div>
      <div>
        <h3>{{ statDefense }}</h3>
        <p>Defense</p>
      </div>
      <div>
        <h3>{{ statSpeed }}</h3>
        <p>Speed</p>
      </div>
    </div>
  </div>
</template>

<style>
*::-webkit-scrollbar {
  width: 10px;
}

*::-webkit-scrollbar-thumb {
  background-color: rgb(179, 179, 179, 0.2);
  border-radius: 10px;
}
#card {
  position: relative;
  width: 100%;
  padding: 30px 20px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.15);
  border-radius: 10px;
  overflow-y: scroll;
}
#card img {
  display: block;
  height: 200px;
  max-width: 250px;
  position: relative;
  margin: 20px auto;
}
.hp {
  width: 80px;
  background-color: #ffffff;
  text-align: center;
  padding: 8px 0;
  border-radius: 30px;
  margin-left: auto;
  font-weight: 400;
}
.poke-name {
  text-align: center;
  font-weight: 600;
}
.types {
  display: flex;
  justify-content: space-evenly;
  margin: 20px 0 25px 0;
}
.hp span,
.types span {
  font-size: 12px;
  letter-spacing: 0.4px;
  font-weight: 600;
}
.types span {
  padding: 5px 20px;
  border-radius: 20px;
  color: #ffffff;
}
.stats {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  text-align: center;
  background-color: #ffffff;
  box-shadow: 0 0px 20px rgba(0, 0, 0, 0.15);
  padding: 20px 0 10px 0;
  border-radius: 30px;
  margin-left: auto;
  font-weight: 400;
}
.stats p {
  color: #404060;
}
.attributes {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  text-align: center;
  color: #686868;
  margin: 0 0 10px 0;
}
.attributes h3 {
  font-size: 24px;
  font-weight: 550;
  margin: 0;
}
</style>
