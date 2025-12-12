<template>
  <div>
    <img v-if="imagen" :src="imagen" alt="No puede visualizar la imagen" />
    <div class="pregunta-container">
      <h1>Pregunta</h1>
      <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
      <p>Recuerda terminar con el signo de interrogación(?)</p>
      <h2>{{ pregunta }}</h2>
      <h1>{{ respuesta }}</h1>
    </div>
  </div>
</template>

<script>
import { consumirAPIFacade } from '@/clients/YesNoClient'
export default {
  data() {
    return {
      pregunta: null,
      respuesta: null,
      imagen: null,
    }
  },
  //opción de OPCION API
  //son observadores de una propiedad Reactiva y se dispara cuando esa propiedad cambia.
  // Cuando la propiedad pregunta cambia, se ejecuta la función definida dentro del observador.
  watch: {
    pregunta(value, oldValue) {
      if (value.includes('?')) {
        //va ha llamar a la API
        this.respuesta = 'Pensando ...'
        this.consumir()
      }
    },
  },
  methods: {
    async consumir() {
      const resp = await consumirAPIFacade()
      console.log('Respuesta final:')
      console.log(resp)

      this.respuesta = resp.answer
      this.imagen = resp.image
    },
  },
}
</script>

<style>
img {
  height: 100vh;
  width: 100vw;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  left: 0; /*esta es para mover la imagen a la derecha */
  top: 0; /*esta es para mover la imagen hacia abajo*/
}
.pregunta-container {
  position: relative;

  /*min-height: 100vh;  altura de toda la pantalla */
  display: flex;
  flex-direction: column; /* elementos uno debajo del otro */
  justify-content: center; /* centrado vertical */
  align-items: center; /* centrado horizontal */
  text-align: center;
  gap: 30px;
  background-color: rgba(255, 255, 255, 0.4); /*color de fondo*/
  padding: 20px;
  border-radius: 20px;
}
input {
  width: 250px;
  padding: 10px;
  border-radius: 20px;
  border: none;
}
input:focus {
  outline: none;
}

h1,
h2,
p {
  color: black;
}
p {
  font-size: 20px;
}
</style>
