<script setup>
defineProps({
  dados: {
    type: Object,
    required: true
  }
})
</script>


<template>
  <div class="info-box" v-if="dados">
    <h3 class="titulo">📍 Endereço</h3>
    <ul>
      <li><strong>Logradouro:</strong> {{ dados?.logradouro }}</li>
      <li><strong>Bairro:</strong> {{ dados?.bairro }}</li>
      <li><strong>Cidade:</strong> {{ dados?.localidade }}</li> 
      <li><strong>Estado</strong>  {{ dados?.uf }}</li>
      <li><strong>CEP:</strong> {{ dados?.cep }}</li>
    </ul>
  </div>
</template>



<style scoped>
.info-box li {
  display: flex;
  justify-content: space-between;
  margin: 6px 0;
  border-left: 4px solid #e1e1e1;
  padding-left: 10px;
}
</style>
