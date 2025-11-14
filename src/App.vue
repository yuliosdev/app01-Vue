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
import { computed } from "vue";

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

const limite = computed(() => {
  return fiesta.asistentes >= fiesta.aforo ? "Aforo Completo" : "Aún hay cupo";
});
const pintar = ref(false);

// <!-- Representación condicional -->
const awesome = ref(true);
const opc = ref("");
const mostrar = ref(false);

// Representación de listas
let users = ["Yulios", "Ana", "Luis", "Marta", "Alisson", "Kristell"];
let backend = [
  {
    id: 1,
    name: "Node.js",
  },
  {
    id: 2,
    name: "Django",
  },
  {
    id: 3,
    name: "Laravel",
  },
];
let frontend = [
  {
    id: 1,
    name: "Vue",
  },
  {
    id: 2,
    name: "React",
  },
  {
    id: 3,
    name: "Angular",
  },
];
let lenguajes = [
  {
    id: 1,
    name: "JavaScript",
    active: true,
  },
  {
    id: 2,
    name: "Python",
    active: true,
  },
  {
    id: 3,
    name: "Pascal",
    active: false,
  },
  {
    id: 4,
    name: "Visual foxpro",
    active: true,
  },
];

// Manejo de Eventos
const enviar = () => {
  console.log("Formulario Enviado");
};

//Enlaces de entrada de formulario
let paises = [];
const pais = ref("");
const save = () => {
  if (pais.value && !paises.includes(pais.value)) {
    paises.push(pais.value);
    pais.value = "";
  } else {
    alert("El país ya está en la lista o el campo está vacío");
  }
};

const number = ref(0);
const playas = ref([]);
const sexo = ref("");

// Modificadores
const cadena = ref("");
const cadena1 = ref("");
const num = ref(0);

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
    <p></p>
    <button @click="agedec">-</button>
    <span class="contador">{{ persona.edad }}</span>
    <button @click="ageinc">+</button>
    <!-- nt139 -->
    <h2>Objeto Reactivo con reactive()</h2>
    <p>Lugar de la fiesta: {{ fiesta.sitio }}</p>
    <p>Número de Asistentes: {{ limite }}</p>
    <button @click="asisdec">-</button>
    <span class="contador">{{ fiesta.asistentes }}</span>
    <button @click="asisinc">+</button>
  </div>
  <div>
    <h2
      :class="{
        'bg-green': pintar,
      }"
    >
      Renderizado Condicional
    </h2>
    <h3 :class="[pintar ? 'bg-red' : 'bg-green', 'text-yellow']">
      Class con varias clases
    </h3>
    <button @click="pintar = !pintar">
      {{ pintar ? "Sin Pintar" : "Pintar" }}
    </button>
  </div>

  <!-- Representación condicional -->
  <div>
    |
    <h2>Representación Condicional</h2>
    <div v-if="awesome">
      <h3>Vue es asombroso!</h3>
    </div>
    <div v-else>
      <h3>Vue no es asombroso!</h3>
    </div>
    <button @click="awesome = !awesome">
      {{ awesome ? "No Like" : "Dar Like" }}
    </button>
  </div>
  <div>
    <h2>Selección con v-if / v-else-if / v-else</h2>
    <button @click="opc = 'a'">A</button>
    <button @click="opc = 'b'">B</button>
    <button @click="opc = 'c'">C</button>
    <p v-if="(tipo = 'a')">Opción seleccionada: {{ opc }}</p>
    <p v-else-if="(tipo = 'b')">Opción seleccionada: {{ opc }}</p>
    <p v-else-if="(tipo = 'c')">Opción seleccionada: {{ opc }}</p>
    <p v-else>Ninguna opción seleccionada</p>

    <button @click="mostrar = !mostrar">
      Da click para {{ mostrar ? "quitar" : "mostrar" }} Mensaje
    </button>
    <template v-if="mostrar">
      <h2>Eres Genial</h2>
      <p>Sigue esforzandote por aprender</p>
    </template>
    <!-- v-show solo funciona con DIV y agrega css -->
    <div v-show="mostrar">Muy pronto lo lograras</div>
  </div>

  <div>
    <h2>Representación de Listas</h2>
    <ol>
      <li v-for="user in users">{{ user }}</li>
    </ol>
    <ul>
      <li v-for="(user, index) in users" :key="index">
        {{ index + 1 }} - {{ user }}
      </li>
    </ul>
    <dl>
      <dt>Backend</dt>
      <dd v-for="{ id, name } in backend">{{ id }} . {{ name }}</dd>
      <dt>frontend</dt>
      <dd v-for="ft in frontend">{{ ft.id }} - {{ ft.name }}</dd>
    </dl>
    <h3>Lenguajes de Programación</h3>
    <template v-for="lang in lenguajes" :key="lang.id">
      <li v-if="lang.active">{{ lang.id }} - {{ lang.name }}</li>
    </template>
  </div>

  <!-- Manejo de eventos -->
  <div>
    <div>
      <h2>Manejo de Eventos</h2>
      <button @click="console.log('Hola desde Vue!')">Mostrar Alerta</button>
      <input
        type="text"
        placeholder="Escribe tu nombre"
        @input="console.log($event.target.value)"
      />
    </div>
    <div @click="console.log('Hiciste Click en el DIV')">
      <p>Control de Eventos</p>
      <button @click.stop="console.log('Hiciste click en el botón')">
        Haz Click Aquí
      </button>
    </div>
  </div>
  <div>
    <h2>Envio de Formularios</h2>
    <form @submit.prevent="enviar">
      <input
        type="text"
        @keyup="console.log('haz presionado una tecla')"
        placeholder="Nombre"
        required
      />
      <input
        type="email"
        @keyup.enter="console.log('haz presionado enter')"
        placeholder="Correo Electrónico"
        required
      />
      <button type="submit">Enviar</button>
    </form>
  </div>
  <div>
    <h2>Enlace de Entrada de Formulario</h2>
    <form @submit.prevent="save">
      <input
        type="text"
        v-model="pais"
        placeholder="Escribe el nombre de un país"
      />
      <button>Agregar País</button>
    </form>
    <p v-if="paises.length">Países :</p>
    <ul>
      <li v-for="(pais, index) in paises" :key="index">
        {{ index }} - {{ pais }}
      </li>
    </ul>
  </div>
  <div>
    <h2>Seleciones un Número</h2>
    <div>
      <label>
        <input type="radio" v-model="number" value="1" />
        Uno
      </label>
    </div>
    <div>
      <label>
        <input type="radio" v-model="number" value="2" />
        Dos
      </label>
    </div>
    <div>
      <label>
        <input type="radio" v-model="number" value="3" />
        Tres
      </label>
    </div>
    <p>Número seleccionado: {{ number }}</p>
  </div>
  <div>
    <h2>Seleccionas tus playa favorita</h2>
    <div>
      <label>
        <input type="checkbox" v-model="playas" value="Copacabana" />
        Copacabana
      </label>
    </div>
    <div>
      <label>
        <input type="checkbox" v-model="playas" value="Ipanema" />
        Ipanema
      </label>
    </div>
    <div>
      <label>
        <input type="checkbox" v-model="playas" value="Mancora" />
        Waikiki
      </label>
    </div>
    <p>Playa favorita: {{ playas }}</p>
  </div>
  <div>
    <h2>Selecciona tu Sexo</h2>
    <div>
      <select v-model="sexo">
        <option value="">Seleccione una Opción</option>
        <option value="Masculino">Masculino</option>
        <option value="Femenino">Femenino</option>
        <option value="Otro">Otro</option>
      </select>
    </div>
    <p>Sexo seleccionado: {{ sexo }}</p>
  </div>
  <div>
    <h2>Modificadores de Entrada</h2>
    <input
      type="text"
      v-model.lazy="cadena"
      placeholder="Escribe algo (lazy)"
    />
    <p>Cadena ingresada: "{{ cadena }}"</p>
    <input
      type="text"
      v-model.trim="cadena1"
      placeholder="Escribe algo (trim)"
    />
    <p>Cadena ingresada: "{{ cadena1 }}"</p>
    <!-- se especifica v-model.numer para convertir la entrada en número -->
    <input
      type="text"
      v-model.number="num"
      placeholder="Escribe un número (number)"
    />
    <button @click="number = num * 2">
      calcular x 2
    </button>
    <p>Número ingresado: {{ number }}</p>
  </div>
</template>

<style scoped>
.bg-red {
  background-color: red;
  color: white;
  padding: 10px;
}
.bg-green {
  background-color: green;
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
.text-yellow {
  color: yellow;
}
.contador {
  margin: 0 15px;
  font-weight: bold;
}
</style>
