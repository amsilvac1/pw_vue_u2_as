<template>
  <div>
    <img
      src="https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif"
      alt="No puede visualizar la imagen"
    />
    <div class="pregunta-container">
      <h1>Pregunta</h1>
      <input type="text" placeholder="Hazme una pregunta" />
      <p>Recuerda terminar con el signo de interrogación(?)</p>
      <h2>Sere millonario?</h2>
      <h1>YES, NO</h1>
    </div>
  </div>
</template>

<script>
export default {}
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
