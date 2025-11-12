<script setup>
const msg01 = "Bienvenido Yulios Dev!";
const msg02 = "<h1>Comencemos con Vue3</h1>";
</script>

<template>
  <div>{{ msg01 }}</div>
  <div v-html="msg02"></div>
</template>

<style scoped></style>
