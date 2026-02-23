<script setup>
import { ref } from 'vue'
import Padre from './components/Padre.vue'

const mostrar = ref(true)
</script>

<template>
  <div class="componentes">
    <h1>Componente App</h1>

    <button @click="mostrar = !mostrar">
      {{ mostrar ? "Desmontar Padre" : "Montar Padre" }}
    </button>

    <Padre v-if="mostrar" />
  </div>
</template>

<style>
.componentes{
  max-width: 600px;
  margin: 3em auto;
}
</style>

