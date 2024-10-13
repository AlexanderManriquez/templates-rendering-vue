<script>
export default {
  name: "Estilos",
  data() {
    return {
      fondo: "",
      colorTexto: "",
      mostrar: true,
      border: 0,
      texto: "Aquí puedes escribir lo que quieras",
      estiloTexto: "",
      opacidad: false,
      tamanosLetra: [
        { label: "Pequeño", value: "16px" },
        { label: "Mediano", value: "20px" },
        { label: "Grande", value: "30px" },
      ],
      tamanoLetra: "20px",
    };
  },
};
</script>

<template>
  <div class="app">
    <div class="estilos">
      <label>Color de Fondo</label>
      <input type="text" v-model="fondo" />

      <label>Color de Texto</label>
      <input type="text" v-model="colorTexto" />

      <div class="checkbox">
        <label>Mostrar Texto</label>
        <input type="checkbox" v-model="mostrar" />
      </div>

      <label>Borde</label>
      <input type="range" v-model="border" min="0" max="75" />

      <label>Contenido Textual</label>
      <textarea
        v-model="texto"
        placeholder="Escribe aquí para modificar el texto"
      ></textarea>

      <label>Tipografía</label>
      <select v-model="estiloTexto">
        <option value="italic">Cursiva</option>
        <option value="normal">Normal</option>
        <option value="oblique">Oblicua</option>
      </select>

      <div class="checkbox">
        <label>Opaco</label>
        <input type="checkbox" v-model="opacidad" />
      </div>

      <label>Tamaño de Letra</label>
      <div class="checkbox">
        <div v-for="(tamano, index) in tamanosLetra" :key="index">
          <input
            type="radio"
            :id="tamano.label"
            name="tamanoLetra"
            :value="tamano.value"
            v-model="tamanoLetra"
          />
          <label :for="tamano.label">{{ tamano.label }}</label>
        </div>
      </div>
    </div>

    <div
      class="caja"
      :class="{ 'opacity-low': opacidad }"
      :style="{
        backgroundColor: fondo,
        color: colorTexto,
        borderRadius: border + 'px',
        fontStyle: estiloTexto,
        opacity: opacidad ? 0.5 : 1,
        fontSize: tamanoLetra 
      }"
    >
      <p
        v-show="mostrar"
        v-if="texto !== 'Aquí puedes escribir lo que quieras'"
      >
        {{ texto }}
      </p>
    </div>
  </div>
</template>

<style>
.app {
  display: flex;
  justify-content: space-around;
}

.estilos {
  width: 40vw;
  height: 60vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2.5rem;
  background-color: black;
  color: #ccc;
}

.caja {
  width: 40vw;
  height: 71.5vh;
  margin: 0 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: opacity 0.5s ease;
}

.opacity-low {
  opacity: 0.5;
}
</style>
