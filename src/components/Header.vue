
<script setup>
import { ref } from 'vue'
const cep = ref('') // controle do input
const loading = ref(false) // Estado de carregamento para a busca
const emit = defineEmits(['dadosClima', 'loading'])

const buscarClima = async () => {
  if (!cep.value) return
  
  // Validação simples do formato de CEP
  const regexCep = /^[0-9]{5}-?[0-9]{3}$/;
  if (!regexCep.test(cep.value)) {
    alert('Por favor, insira um CEP válido!');
    return;
  }

  // Limpar resultados anteriores
  emit('dadosClima', null)

  try {
    emit('loading', true) // dispara que está carregando
    //loading.value = true;  // Inicia o carregamento
    // 1. Limpa o CEP, removendo o hífen
    const cepLimpo = cep.value.replace('-', '');

    console.log('📦 CEP ionformado:', cepLimpo)
    // local
    //const response = await fetch(`http://127.0.0.1:5000/clima?cep=${cep.value}`)
    const response = await fetch(`https://clima2api.up.railway.app/clima?cep=${cepLimpo}`);
    const dados = await response.json()
    console.log('📦 Resultado da API:', dados)

    // Emite os dados para o componente pai
    emit('dadosClima', dados)
    emit('loading', false) // termina o carregamento
  } catch (error) {
    console.error('❌ Erro ao buscar clima:', error)
  }finally {
    //loading.value = false;  // Finaliza o carregamento
    
  }
}
</script>

<template>
  <header class="header">
     <div class="menu-icon" aria-label="Abrir menu">☰</div>

    <div class="logo">
      <strong>LOCALCLIMA</strong>
      <p class="subtitle">A Company</p>
    </div>

    <div class="search-box">
      <input 
      v-model="cep" 
      @keyup.enter="buscarClima" 
      type="text" 
      placeholder="Busque por uma cep..."
      aria-label="Digite o CEP para buscar o clima"
      :disabled="loading" />
      
      <span class="search-icon" @click="buscarClima" role="button" aria-label="Buscar clima">🔍</span>    
    </div>

    <button class="login-button">
      <span class="login-icon">👤</span>
      Faça seu login
    </button>
  </header>
</template>

<style scoped>
.login-icon {
  display: inline-block;
  filter: brightness(0) invert(1);
}

.header {
  display: flex;
  align-items: center;
  background-color: #007ac2;
  padding: 10px 20px;
  color: white;
  gap: 15px;
}

.menu-icon {
  font-size: 24px;
  cursor: pointer;
}

.logo {
  display: flex;
  flex-direction: column;
  font-size: 18px;
  line-height: 1;
}

.subtitle {
  font-size: 10px;
  margin: 0;
}

.search-box {
  flex: 1;
  display: flex;
  align-items: center;
  background-color: #0066a3;
  padding: 8px 12px;
  border-radius: 5px;
  margin: 0 20px;
}

.search-box input {
  flex: 1;
  border: none;
  background: transparent;
  color: white;
  outline: none;
  font-size: 14px;
}

.search-icon {
  margin-left: 8px;
  color: #f6f2f2;
}

.login-button {
  background: transparent;
  color: white;
  border: 1px solid white;
  border-radius: 4px;
  padding: 6px 12px;
  font-size: 14px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 5px;
}

.login-icon {
  font-size: 16px;
  color: white;
}
</style>
