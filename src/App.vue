<script setup>
const msg01 = "Bienvenido Yulios Dev!";
const msg02 = "<h1>Comencemos con Vue3</h1>";
const clase = "bg-red"
</script>

<template>
  <div>{{ msg01 }}</div>
  <div v-html="msg02"></div>
  <div :class="clase">Este div tiene una clase dinámica</div>
</template>

<style scoped>
.bg-red {
  background-color: red;
  color: white;
  padding: 10px;
}
</style>
