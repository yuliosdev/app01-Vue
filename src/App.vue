<script setup>
const msg01 = "Bienvenido Yulios Dev!";
const msg02 = "<h1>Comencemos con Vue3</h1>";
const clase = "bg-red";
const idtext = "texto";
const id = "parrafo";
const isDisabled = true;
// Reactividad en Vue3
import { ref } from "vue";
import { reactive } from "vue";

const contador = ref(0);

function incrementar() {
  contador.value++;
  console.log(contador.value);
}
function decrementar() {
  contador.value--;
  console.log(contador.value);
}

// ejemplo con objetos reactivos
const persona = ref({
  nombre: "Yulios",
  edad: 30,
});
function ageinc() {
  persona.value.edad++;
  console.log(persona.value.edad);
}
function agedec() {
  persona.value.edad--;
  console.log(persona.value.edad);
}

const fiesta = reactive({
  sitio: "Lima",
  asistentes: 25,
  aforo: 50,
});

function asisinc() {
  fiesta.asistentes++;
  console.log(fiesta.asistentes);
}
function asisdec() {
  fiesta.asistentes--;
  console.log(fiesta.asistentes);
}
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

  <!-- Fundamentos de la reactividad en Vue3 -->
  <div>
    <button @click="decrementar">Decrementar</button>
    <span class="contador"> {{ contador }} </span>
    <button @click="incrementar">Incrementar</button>
  </div>

  <div>
    <h2>Objeto Reactivo en VUe</h2>
    <p>Nombre: {{ persona.nombre }}</p>
    <p>
      Edad: {{ persona.edad >= 18 ? "Es mayor de Edad." : "Es menor de edad." }}
    </p>
    <button @click="agedec">-</button>
    <span class="contador">{{ persona.edad }}</span>
    <button @click="ageinc">+</button>
    <!-- nt139 -->
    <h2>Objeto Reactivo con reactive()</h2>
    <p>Lugar de la fiesta: {{ fiesta.sitio }}</p>
    <p>
      Número de Asistentes:
      {{
        fiesta.asistentes >= fiesta.aforo ? "Aforo Completo" : "Aún hay cupo"
      }}
    </p>
    <button @click="asisdec">-</button>
    <span class="contador">{{ fiesta.asistentes }}</span>
    <button @click="asisinc">+</button>
  </div>
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
.contador {
  margin: 0 15px;
  font-weight: bold;
}
</style>
