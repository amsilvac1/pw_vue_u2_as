<template>
  <div class="container">
    <PokemonImagen :pokemonId="pokemonGanador" />
    <PokemonOpciones
      v-on:seleccionado="evaluarGanador($event)"
      :listaPokemons="pokemonArr"
    />
    <h1>{{ mensaje }}</h1>
  </div>
</template>

<script>
import PokemonImagen from '@/components/PokemonImagen.vue'
import PokemonOpciones from '@/components/PokemonOpciones.vue'
import {
  obetenerVectorPokemonFachada,
  obtenerAleatorioFachada,
} from '../clients/PokemonClients.js'
export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  data() {
    return {
      pokemonArr: [],
      pokemonGanador: null,
      mensaje: null,
    }
  },
  mounted() {
    this.iniciarJuego()
  },

  methods: {
    async iniciarJuego() {
      this.pokemonArr = await obetenerVectorPokemonFachada()

      const idAleatorio = obtenerAleatorioFachada(0, 3)
      this.pokemonGanador = this.pokemonArr[idAleatorio].id
      this.mensaje = null
    },
    evaluarGanador(idGanador) {
      console.log('Valor recibido desde padre')
      console.log(idGanador)
      if (idGanador === this.pokemonGanador) {
        console.log('ganador')
        this.mensaje = '¡¡¡ Selecionaste el pokemon Correcto !!!'
        this.iniciarJuego()
      } else {
        console.log('perdedor')
        this.mensaje = 'Selecionaste el pokemon Incorrecto'
      }
    },
  },
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
h1 {
  border-radius: 5px;
  border: solid 1px;
  color: coral;
}
</style>
