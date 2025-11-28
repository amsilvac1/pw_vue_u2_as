<template>
  <div>
    <label for="id_nombre">Nombre</label>
    <!-- el valor que pongo a la directiva v-model es una propiedad reactiva-->
    <input v-model="nombre" id="id_nombre" type="text" />
    <p>{{ nombre }}</p>

    <label for="id_apellido">Apellido</label>
    <input v-model="apellido" id="id_apellido" type="text" />

    <button @click="imprimirNombre()">Imprimir nombre</button>
    <h1>{{ arreglo }}</h1>
    <button @click="agregarEstudiante">Agregar estudiante</button>
    <ul>
      <li
        v-show="nombre !== null"
        v-for="{ nombre, apellido } in arreglo"
        :key="nombre"
      >
        {{ nombre }} - {{ apellido }}
      </li>
    </ul>
    <h2>Tabla</h2>
    <table border="1">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="{ nombre, apellido } in arreglo" :key="nombre">
          <td>{{ nombre }}</td>
          <td>{{ apellido }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
      arreglo: [],
    }
  },
  methods: {
    imprimirNombre() {
      console.log(this.nombre)
      console.log(this.apellido)
    },
    agregarEstudiante() {
      const estu = {
        nombre: this.nombre,
        apellido: this.apellido,
      }
      console.log('Agregar estudiante')
      console.log(estu)
      this.arreglo.push(estu)
      this.limpiarFormulario()
    },
    limpiarFormulario() {
      this.nombre = ''
      this.apellido = ''
    },
  },
}
</script>

<style></style>
