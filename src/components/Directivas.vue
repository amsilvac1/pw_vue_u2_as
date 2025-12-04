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
    <hr />
    <label for="id_nombre_1">Nombre</label>
    <input v-model="nombre" id="id_nombre_1" type="text" />
    <label for="id_apellido_1">Apellido</label>
    <input
      v-model="apellido"
      v-on:keypress.enter="agregarEstudiante1"
      id="id_apellido_1"
      type="text"
    />
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
    agregarEstudiante1(event) {
      console.log('Evento')
      if (event.charCode !== 13) {
        return
      }
      const estu = {
        nombre: this.nombre,
        apellido: this.apellido,
      }
      this.arreglo.push(estu)
      this.limpiarFormulario()
      console.log('Enter presionado')
      console.log('Agregar estudiante 1')
      console.log(event)
      console.log(event.charCode)
    },
    limpiarFormulario() {
      this.nombre = ''
      this.apellido = ''
    },
  },
}
</script>

<style></style>
