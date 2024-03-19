<script setup>
import {ref, watch} from 'vue';
import CardAtracaoTuristica from '@/components/CardAtracaoTuristica.vue';

let atracoesTuristicas = ref([])

fetch('/atracoes.json')
    .then(resposta => resposta.json())
    .then(dados => atracoesTuristicas.value = dados)

const mensagem = ref(null)
watch(mensagem, (novaMensagem) => {
  if (novaMensagem) {
    setTimeout(() => mensagem.value = null, 2000)
  }
})

function enviarMensagem(novaMensagem) {
  mensagem.value = novaMensagem
}

</script>
<template>
  <h1>Atrações turísticas</h1>
  <p>Total: {{ atracoesTuristicas.length }}</p>
  <div class="alert alert-danger" role="alert" v-if='mensagem'>{{ mensagem }}</div>
  <CardAtracaoTuristica
      v-for='(atracaoTuristica, indice) in atracoesTuristicas'
      @enviar-mensagem='enviarMensagem'
      :key='`atracaoTuristica${indice}`'
      :atracaoTuristica='atracaoTuristica'/>
</template>

<style scoped>

</style>
