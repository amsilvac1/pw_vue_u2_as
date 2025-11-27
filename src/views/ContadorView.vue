<template>
  <div>
    <!-- v-bind, transofrma todo a JS-->
    <!-- directiva-->
    <Contador
      tit="Contador 1"
      v-bind:inicio="4 + 4"
      :mostrar="true"
      :mostrar2="true"
    />
    <Contador
      tit="Contador 2"
      :inicio="10"
      :mostrar="false"
      :mostrar2="false"
    />
  </div>
</template>

<script>
import Contador from '../components/Contador.vue'
export default {
  components: {
    Contador,
  },
}
</script>

<style></style>
