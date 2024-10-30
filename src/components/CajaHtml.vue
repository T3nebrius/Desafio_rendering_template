<template>
    <div>
    <div class="cajaCentral">
        <div class="DivEntrada1">
          <label> Color de fondo </label>
          <input type="color" v-model="colorFondoCajaReactiva" class="entrada1">
        </div>  
        <div class="DivEntrada1">
          <label> Color de texto </label>
          <input type="color" v-model="colorLetraCajaReactiva" class="entrada1">
      </div>  
      <div class="DivEntrada1">
          <label> Mostrar texto </label>
          <input type="checkbox" v-model="mostrar">
      </div>  
      <div class="DivEntrada1">
          <label> Borde </label>
          <input type="range" v-model="bordeCajaReactiva" class="entrada1">
      </div>  
      <div class="DivEntrada1">
          <label> Contenido textual </label>
          <textarea v-model="textoCajaReactiva" class="entrada1"></textarea>
      </div>  
      <div class="DivEntrada1">
          <label> Tipografia </label>
          <select v-model="tipografiaSeleccionada" class="entrada1" >
            <option v-for="(element, index) in tipografia" :key="index">{{element}}</option>
          </select>
      </div>  
      <div class="DivEntrada1">
          <label> Opaco </label>
          <input type="checkbox" v-model="esOpaco">
      </div>
      <div class="DivEntrada1">
          <label> Tamaño de letra </label>
          <div>
            <input type="radio" id="pequeño" value="15px" v-model="tamañoLetra">
            <label for="pequeño"> Pequeño </label>
            <input type="radio" id="mediano" value="20px" v-model="tamañoLetra">
            <label for="mediano"> Mediano </label>
            <input type="radio" id="grande" value="25px" v-model="tamañoLetra">
            <label for="grande"> Grande </label>
          </div>
      </div>
    </div>
    <div :style="{backgroundColor: colorFondoCajaReactiva, color: colorLetraCajaReactiva, borderRadius:bordeCajaReactiva+'%'}" class="cajaReactiva">
       <p :style="{fontStyle: tipografiaSeleccionada, fontSize: tamañoLetra, opacity: opacidadTexto, display: mostrarTexto }" class="textoCaja">{{ textoCajaReactiva }} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CajaHtml',
  data(){
    return {
      tipografia: ["normal","italic","oblique"],
      tipografiaSeleccionada: "",
      colorFondoCajaReactiva: "",
      colorLetraCajaReactiva: "",
      textoCajaReactiva: "",
      bordeCajaReactiva: 0,
      tamañoLetra: "15px",
      esOpaco: false,
      mostrar: "none"
    }
  },
  props: {
  },
  computed: {
    opacidadTexto() {
      return this.esOpaco ? 1 : 0.4; 
    },
    mostrarTexto(){
      return this.mostrar ? "block" : "none";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cajaCentral{
  background-color: #2f4f4e;
  display: inline-block;
  color: white;
  height: 450px;
  width: 350px;
  max-width: 350px;
  padding-top: 3%;
}

.DivEntrada1{
  text-align: left;
  margin-left: 10%;
  margin-top: 3%;
}

.entrada1{
  width: 90%;
}

.cajaReactiva{
  display: inline-block;
  color: white;
  width: 400px;
  height: 400px;
  margin-left: 30%;
  overflow: hidden; 
  text-align: center; 
  word-wrap: break-word; 
  padding: 10px; 
  box-sizing: border-box; 
}
</style>
