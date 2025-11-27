<template>
  <div>
    <h1>{{ titulo }}</h1>
    <h1>{{ tit }}</h1>

    <p>{{ numero }} <sup>2</sup>= {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>2</sup>= {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>2</sup>= {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>3</sup>= {{ calculaCubo }}</p>
    <p>{{ numero }} <sup>3</sup>= {{ obtenerCubo() }}</p>
    <div>
      <!--directivas -->
      <button v-on:click="incrementar">+1</button>
      <button @:click="decrementar">-1</button>
      <!--v-if Recibe un bolean -->
      <button v-if="mostrar">prueba</button>
      <!--visualemnte v-if y v-show se ve igual pero el v-if ocntruye o no contruye el elemento pero el v-show solo lo oculta poniendo un estilo-->
      <button v-show="mostrar2">prueba2</button>
    </div>
  </div>
</template>

<script>
//estructuras por defectos para de declarar opcion mpa

export default {
  //propiedades reactivas
  data() {
    return {
      numero: this.inicio,
      titulo: 'Contador',
    }
  },
  //metodos
  methods: {
    obtenerCuadrado() {
      console.log('Entro a obtener cuadrado')
      return this.numero * this.numero
    },
    obtenerCubo() {
      return this.numero * this.numero * this.numero
    },
    decrementar() {
      this.numero--
    },
    incrementar() {
      console.log(this.tit)
      this.numero++
    },
  },
  //propiedades computadas
  computed: {
    calculaCuadrado() {
      console.log('Entro a propiedad computada')
      return this.numero * this.numero
    },
    calculaCubo() {
      return this.numero * this.numero * this.numero
    },
  },

  //declaracion basica de props
  /*props: ['tit', 'inicio', 'mostrar', 'mostrar2'], */
  //forma mas especfiica de declarar props
  props: {
    tit: String,
    inicio: {
      type: Number,
      default: 99,
      validator(value) {
        return value > 10
      },
    },
    mostrar: Boolean,
    mostrar2: Boolean,
  },
  //Los tipos que ae puede mandar en props:
  // String, Number, Boolean, Array, Object, Date, Funcion, BigInt
}
</script>

<style></style>
