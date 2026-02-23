
<script setup>
import { ref, onMounted, onUpdated, onBeforeUnmount } from 'vue'
import Hijo from './Hijo.vue'

const mensajePadre = ref("Hola desde el componente padre")
const mensajeHijo = ref("")
const estadoCiclo = ref("Creado")

const mostrarConfirmacion = ref(false)
let timeoutId = null

const recibirRespuesta = (mensaje) => {
  mensajeHijo.value = mensaje

  // Mostrar confirmación visual
  mostrarConfirmacion.value = true

  // Limpiar timeout anterior si existe
  if (timeoutId) clearTimeout(timeoutId)

  timeoutId = setTimeout(() => {
    mostrarConfirmacion.value = false
  }, 3000)
}

// mounted
onMounted(() => {
  console.log("Padre montado")
  estadoCiclo.value = "Mounted"
})

// updated
onUpdated(() => {
  console.log("Padre actualizado")
  estadoCiclo.value = "Updated"
})

// beforeUnmount
onBeforeUnmount(() => {
  console.log("Padre se va a desmontar")
  estadoCiclo.value = "Before Unmount"

  // limpieza importante
  if (timeoutId) clearTimeout(timeoutId)
})
</script>

<template>
  <div>
    <h2>Componente Padre</h2>

    <!-- Estado visual del ciclo de vida -->
    <div class="estado">
      <p><strong>Estado actual:</strong> {{ estadoCiclo }}</p>
    </div>

    <!-- Mensaje temporal -->
    <transition name="fade">
      <p v-if="mostrarConfirmacion" class="confirmacion">
        Mensaje recibido 
      </p>
    </transition>

    <Hijo 
      :mensaje="mensajePadre"
      @respuestaHijo="recibirRespuesta"
    />

    <p v-if="mensajeHijo">
      Respuesta del hijo: {{ mensajeHijo }}
    </p>
  </div>
</template>



<style scoped>
.estado {
  background-color: #f4f4f4;
  padding: 2em;
  margin-block: 1em;
  border-radius: 5px;
}

.confirmacion {
  background-color: #d4edda;
  color: #155724;
  padding: 1em;
  border-radius: 5px;
  margin-bottom: 1em;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
