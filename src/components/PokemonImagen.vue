<template>
  <div class="pokemon-container">
    <img :src="srcImagen" alt="No se puede renderizar" />
  </div>
</template>

<script>
export default {
  /*Desmontaje de un componente */
  beforeUnmount() {
    console.log('beforeUnmount: justo antes de que el componente se destruya')
  },
  unmounted() {
    console.log(
      'unmounted: se ejecuta cuando ya fue removido el DOM y destrido'
    )
  },
  props: {
    pokemonId: {
      type: Number,
      required: true,
    },
  },
  computed: {
    srcImagen() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
    },
  },
}
</script>

<style scoped>
img {
  height: 200px;
}
.pokemon-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
