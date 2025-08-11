<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import ClimaPainel from './views/ClimaPainel.vue'
import { ref } from 'vue'

// Criando uma variável reativa para armazenar os dados do clima
const dadosClima = ref(null)

// Função para atualizar os dados do clima
const atualizarDados = (dados) => {
  dadosClima.value = dados
}

</script>

<template>
  <Header @dadosClima="atualizarDados" />
  <main>
    <h1>Climajá - Your Weather App</h1>
    <p>
      Search for a zip code and explore weather data and forecasts.</p>
    
    <!-- Condicional para garantir que dadosClima não seja null antes de passar para o componente -->
    <ClimaPainel v-if="dadosClima" :dados="dadosClima" />

  </main>

  <Footer />
</template>


<style scoped>
/* Layout geral da página */
:global(body, html, #app) {
  height: 100%;
  margin: 0;
  padding: 0;
}

:global(#app) {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

/* Faz o main crescer para ocupar o espaço entre Header e Footer */
main {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 40px 20px;
  background-color: #f5f5f5;
  text-align: center;
}
</style>