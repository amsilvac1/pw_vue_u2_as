<template>
  <div class="view-container">
    <h2>Prueba</h2>
    <Directivas />
  </div>
</template>

<script>
import Directivas from '@/components/Directivas.vue'
export default {
  components: {
    Directivas,
  },
}
</script>

//Scoped permite que solo los estilos funcionene dentro de esta clase, no
globalmente
<style scoped>
.view-container {
  min-height: 100dvh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

h2 {
  font-size: 50px;
}
</style>
