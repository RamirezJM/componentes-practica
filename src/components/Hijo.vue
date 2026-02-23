
<script setup>
import { defineProps, defineEmits, onMounted } from 'vue'

// recibir prop
const props = defineProps({
  mensaje: String
})

// definir evento
const emit = defineEmits(['respuestaHijo'])

// función que emite evento
const enviarRespuesta = () => {
  emit('respuestaHijo', 'Hola padre, aquí el hijo')
}

// hook
onMounted(() => {
  console.log("Hijo montado")
})
</script>

<template>
  <div>
    <h3>Componente Hijo</h3>

    <p>Mensaje recibido: {{ mensaje }}</p>

    <button @click="enviarRespuesta">
      Enviar respuesta al padre
    </button>
  </div>
</template>
