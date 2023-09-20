<script setup>
import { ref } from "vue";

let num = ref(0);
</script>

<template>
  <div class="main">
    <router-view></router-view>
  </div>
</template>

<style>
footer {
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
}
</style>
