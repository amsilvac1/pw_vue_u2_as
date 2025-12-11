<template>
  <div>
    <!--<ContadorView />-->
    <!--<DirectivasView />-->
    <PreguntaView />
  </div>
</template>

<script>
import ContadorView from '../src/views/ContadorView.vue'
import DirectivasView from './views/DirectivasView.vue'
import PreguntaView from './views/PreguntaView.vue'
export default {
  components: {
    ContadorView,
    DirectivasView,
    PreguntaView,
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
