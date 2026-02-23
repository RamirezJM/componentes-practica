# componentes-practica
ejercicio 1 / Modulo VII - Vue

ejercicio desplegado: https://ramirezjm.github.io/componentes-practica/

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
![Static Badge](https://img.shields.io/badge/HTML5-%23f06529)
![Static Badge](https://img.shields.io/badge/CSS3-%232965f1)
![Static Badge](https://img.shields.io/badge/Javascript-%23f0db4f)
![Static Badge](https://img.shields.io/badge/Vue-2342b883)

## Paso de datos con props
Las props permiten enviar datos del componente padre al hijo (flujo descendente).
En el padre
```HMTL
<Hijo :mensaje="mensajePadre" />
```
- mensaje es la prop que el hijo espera.
- mensajePadre es el valor reactivo que se envía.

en el hijo
```Javascript
const props = defineProps({
  mensaje: String
})
```
El hijo recibe ese dato y lo puede usar en su template:
```HTML
<p>{{ mensaje }}</p>
```

<div>
  <img src="public/images/app.jpg" width=500>
</div>

## Emisión de eventos
La comunicación inversa (del hijo al padre) se hace mediante eventos personalizados.

```Javascript
// definir evento
const emit = defineEmits(['respuestaHijo'])

// función que emite evento
const enviarRespuesta = () => {
  emit('respuestaHijo', 'Hola padre, aquí el hijo')
}
```
- 'respuestaHijo' es el nombre del evento.
- El segundo argumento es el dato que se envía al padre.

en el padre
```HTML
<Hijo @respuestaHijo="recibirRespuesta" />
```
El padre “escucha” el evento y ejecuta:
```Javascript
const recibirRespuesta = (mensaje) => {
  mensajeHijo.value = mensaje
}
```

<div>
  <img src="public/images/app3.jpg" width=500>
</div>

## Hooks del ciclo de vida

#### onMounted()
Se ejecuta cuando el componente ya fue renderizado y está en el DOM.
```Javascript
onMounted(() => {
  console.log("Padre montado")
})
```

#### onUpdated()
Se ejecuta cada vez que el componente se vuelve a renderizar por un cambio reactivo.
```Javascript
mensajeHijo.value = mensaje
```

#### onBeforeUnmount()
Se ejecuta justo antes de que el componente sea eliminado del DOM.
en el ejercicio:
```Javascript
onBeforeUnmount(() => {
  clearTimeout(timeoutId)
})
```
<div>
  <img src="public/images/consola1.jpg" width=500>
</div>


### Clonar el repositorio

  ```bash
   git clone https://github.com/RamirezJM/componentes-practica.git
   cd componentes-practica
  ```

### Instalar dependencias

```bash
npm install
```

### Levantar el servidor

```bash
npm run dev
```
