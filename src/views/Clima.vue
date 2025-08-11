<template>
    <div class="info-box" v-if="dados && localizacao">
        <h3 class="titulo">
            🌤️ Tempo agora em {{ localizacao.localidade }}, {{ localizacao.uf }} <span>📍</span>
        </h3>

        <div class="temperatura">
            <div class="icone">
                {{ dados.is_day === 1 ? '☀️' : '🌙' }}
            </div>
            <div class="valor">{{ Math.round(dados.temperatura) }}<sup>º</sup></div>
        </div>

        <ul class="detalhes">
            <li>
                <span class="label">🌬️ <strong>Vento:</strong></span>
                <span>{{ dados.windspeed }} km/h</span>
            </li>
            <li>
                <span class="label">🧭 <strong> Direção do Vento:</strong></span>
                <span translate="no">{{ dados.winddirection }}° - {{(windDirection(dados.winddirection))}}</span>
            </li>

            <li>
                <span class="label">☁️ <strong>Condição:</strong></span>
                <span>{{ dados.is_day === 1 ? 'Dia': 'Noite'}}</span>
            </li>

            <li>
                <span class="label">🌈 <strong>Previsão de Arco-Íris:</strong></span>
                <span class="apagado">Sem dados de formação de arco-íris!</span>
            </li>
        </ul>

    </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  dados: Object,
  localizacao: Object
})

// Função para converter direção do vento em graus para pontos cardeais
const windDirection = (degrees) => {
  if (degrees >= 0 && degrees < 45) return "N";
  if (degrees >= 45 && degrees < 90) return "NE";
  if (degrees >= 90 && degrees < 135) return "E";
  if (degrees >= 135 && degrees < 180) return "SE";
  if (degrees >= 180 && degrees < 225) return "S";
  if (degrees >= 225 && degrees < 270) return "SW";
  if (degrees >= 270 && degrees < 315) return "W";
  if (degrees >= 315 && degrees < 360) return "NW";
  return "Desconhecido"; // Caso algum valor fora do intervalo esperado seja passado
}


</script>

<style scoped>
.clima-box {

    padding: 20px;
    border-radius: 10px;
    width: 320px;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    font-family: sans-serif;
    color: #222;
}
.temperatura {
    display: flex;
    align-items: center;
    font-size: 48px;
    font-weight: bold;
    color: #444;
}
.temperatura .icone {
    font-size: 32px;
    margin-right: 10px;
}
.detalhes {
    list-style: none;
    padding: 0;
    margin: 15px 0;
    font-size: 14px;
}

.detalhes li {
    display: flex;
    justify-content: space-between;
    margin: 6px 0;
    border-left: 4px solid #e1e1e1;
    padding-left: 10px;
}
.apagado {
    color: #9b9797;
    font-style: italic;
}



</style>
