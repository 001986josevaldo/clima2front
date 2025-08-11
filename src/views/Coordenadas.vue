<template>
  <div class="info-box" v-if="dados">
    <h3 class="titulo">🧭 Coordenadas Geográficas</h3>
    <li><strong>Latitude:</strong> {{ dados.lat }}</li>
    <li><strong>Longitude:</strong> {{ dados.lon }}</li>
    <li><strong>Elevação:</strong> {{ elevation }} m</li>
  </div>
</template>

<script setup>
defineProps({
  dados: {
    type: Object,
    required: true
  },
  elevation: {
    type: Number,
    required: true
  }
})
</script>

<style scoped>
.info-box li {
    display: flex;
    justify-content: space-between;
    margin: 6px 0;
    border-left: 4px solid #e1e1e1;
    padding-left: 10px;
}
</style>
