<template>
  <div class="container">
    <PokemonImagen v-if="destruir" :pokemonId="pokemonGanador" />
    <PokemonOpciones
      v-on:seleccionado="evaluarGanador($event)"
      :listaPokemons="pokemonArr"
    />
    <h1>{{ mensaje }}</h1>

    <button @click="destruirImagen">Destruir</button>
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
      destruir: true,
    }
  },
  /*Crea el componente */
  beforeCreate() {
    console.log('beforeCreate: apenas inicia la instancia del componenente')
  },
  created() {
    console.log(
      'created: ya se resolvieron el data, computed, metohos, watch, una vez ejecutados estos se ejecuta el create'
    )
  },
  /*Montaje del componente */
  beforeMount() {
    console.log(
      'beforeMount: Se ejecuta justo antes de renderizar el primer render de un elemento HTML'
    )
  },
  mounted() {
    console.log('mounted: cuando el componenete ya se renderizó')
    this.iniciarJuego()
  },
  /*Actualización de un componente */
  beforeUpdate() {
    console.log(
      'beforeUpdate: cuando cambio un data/props y vue está por re-renderizar'
    )
  },
  updated() {
    console.log('updated: es cuando ya se actualizó,tras la re-renderización')
  },

  /*Desmontaje de un componente */
  beforeUnmount() {
    console.log('beforeUnmount: justo antes de que el componente se destruya')
  },
  unmounted() {
    console.log(
      'unmounted: se ejecuta cuando ya fue removido el DOM y destrido'
    )
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

    destruirImagen() {
      this.destruir = false
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
