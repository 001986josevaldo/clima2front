<script setup>
import Localizacao from './Localizacao.vue'
import Coordenadas from './Coordenadas.vue'
import Clima from './Clima.vue'

defineProps({
  dados: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="info-container" v-if="dados">
    <!-- Exibir os dados do clima aqui -->
    <!-- <h1>Informações do Clima</h1> -->
    
    <Localizacao 
      v-if="dados && dados.endereco" 
      :dados="dados.endereco" 
      :key="dados.endereco.cep" />
    
    <Coordenadas 
      :dados="dados.geolocalizacao" 
      :elevation="dados.clima.elevation" 
      :key="dados.geolocalizacao.lat" />
    
      <Clima
      :dados="dados.clima"
      :localizacao="dados.endereco"
      :key="dados.clima"
    /> 
  </div>
</template>


<!-- <template>
  <div class="info-container">
    <h1>Informações do Clima</h1>
    <Localizacao :dados="dados.dadosCep" :key="dados.dadosCep?.cep" />
    <Coordenadas :dados="dados.coordenadas" :key="dados.coordenadas?.latitude" />
    <Clima
      :dados="dados.clima"
      :localizacao="dados.dadosCep"
      :key="dados.clima"
    />
  </div>
</template> -->

<style scoped>
.info-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  padding: 20px;

  justify-content: space-between;
}

.info-box {
  background: #c3d0ed;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  padding: 20px;
  width: 300px;
  font-family: sans-serif;
  justify-content: space-between;
}

.info-box h3 {
  margin-top: 0;
  font-size: 16px;
  font-weight: bold;
  color: #007ac2;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 5px;
}

.info-box strong {
  font-weight: bold;
}


</style>

