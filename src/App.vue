<script setup>
const msg01 = "Bienvenido Yulios Dev!";
const msg02 = "<h1>Comencemos con Vue3</h1>";
const clase = "bg-red";
const idtext = "texto";
const id = "parrafo";
const isDisabled = true;
</script>

<template>
  <div>{{ msg01 }}</div>
  <div v-html="msg02"></div>
  <div :class="clase">Este div tiene una clase dinámica</div>
  <p :id="idtext">Este párrafo tiene un id dinámico</p>
  <p :id>Azulito como cielo</p>
  <!--cuando de id es igual a la variable id solo va :id -->
  <button :disabled="isDisabled">Hazme Click</button>
  <p>{{ isDisabled ? "El boton está Inactivo" : "El boton esta activo" }}</p>

  
</template>

<style scoped>
.bg-red {
  background-color: red;
  color: white;
  padding: 10px;
}

#texto {
  font-size: 20px;
  font-weight: bold;
}

#parrafo {
  background-color: blue;
  color: white;
  padding: 10px;
}
</style>
