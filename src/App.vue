<script setup>
import { ref , computed} from 'vue'
let nombre = "Angel";
let activo = false;
let colorDinamico = "color: green";
const listaNumeros = ref([]);

//Metodo click

const contador = ref(0);

let aumenta = () =>{
  contador.value++;
}

let disminuye = () => {
  contador.value--;
  
}

let resetear = () =>{
  contador.value = 0
}

let agregar = () => {
if(listaNumeros.value == 0){
  
}
listaNumeros.value.push(contador.value)
}

const existente = computed(() =>{
  const existe = listaNumeros.value.find((num) => num === contador.value);
  if (existe == undefined) return false
  return true ;
});


const classCounter = computed(() => {
   
  if (contador.value === 0){
    return "zero";
  }
  if (contador.value > 0){
    return "positivo";
  }
  if (contador.value < 0) {
    return "negativo";
  }
});

</script>

<template>
  <div class="container-fluid">

  <h1>Hola {{nombre.toUpperCase()}}</h1>
  <h2 :style="colorDinamico">Mi primera aplicacion en VueJS</h2> <!-- El v-bine se puede omitir con :-->
  <p v-if="activo === true"> Estoy Activo</p>                    <!--Con este se ""comentaria""-->
  <p v-else-if="activo === false"> Estoy Inactivo</p>
  <p v-else>Estoy nulo </p>
  <p v-show="activo"> Estoy activo v-show</p> <!-- Con este se la clase d-none-->
    
  <h2 :class="classCounter">{{contador}}</h2>

  <div class="btn=group">
    <button class="btn btn-success" @click="aumenta">Aumentar + </button>
    <button class="btn btn-danger" @click="disminuye">Disminuir - </button>
    <button class="btn btn-primary" @click="resetear">Resetear 0</button>
    <button class="btn btn-info" :disabled="existente" @click="agregar">Agregar ✰</button>

  </div>
 
 <h1>{{listaNumeros}}</h1>

 <ul class="d-none">
  <li v-for="(numero, index) in listaNumeros" :key="index">
      {{numero}}
  </li>
 </ul>
</div>

</template>


<style>
h1 {
  color: rgb(20, 155, 4);
}

.positivo{
  color: green;
}

.negativo{
  color: red;
}

.zero {
  color: white;
}

</style>