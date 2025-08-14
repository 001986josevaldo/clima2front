<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import ClimaPainel from './views/ClimaPainel.vue'
import { ref, nextTick } from 'vue'

// Criando uma variável reativa para armazenar os dados do clima
const dadosClima = ref(null)

const carregando = ref(false)  // <-- estado de loading

// Função para atualizar os dados do clima
const atualizarDados = (dados) => {
  dadosClima.value = dados
}
const setCarregando = async (status) => {
  carregando.value = status
  if (status) {
    // Resetando dadosClima para que desapareça o painel antes de mostrar carregando
    dadosClima.value = null
    // Força atualização do DOM
    await nextTick()
  }
}
</script>+

<template>
  <Header @dadosClima="atualizarDados" @loading="setCarregando" />

  <main>
    <h1>LOCAL CLIMA - Your Weather App</h1>
    <p >
      Informe um CEP para buscar os dados do clima e explore informações sobre temperatura, vento e previsões.
    </p>
    <!-- Tela de carregamento -->
    <div v-if="carregando" class="loading">
      🔄 Loading data, please wait...
    </div>
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

.loading {
  font-size: 1.2rem;
  margin: 20px 0;
  color: #555;
}
</style>