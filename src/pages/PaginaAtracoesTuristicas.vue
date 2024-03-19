<script setup>
import {ref} from 'vue';
import CardAtracaoTuristica from '@/components/CardAtracaoTuristica.vue';

let atracoesTuristicas = ref([])

fetch('/atracoes.json')
    .then(resposta => resposta.json())
    .then(dados => atracoesTuristicas.value = dados)
</script>
<template>
  <h1>Atrações turísticas</h1>
  <p>Total: {{ atracoesTuristicas.length }}</p>
  <CardAtracaoTuristica
      v-for='(atracaoTuristica, indice) in atracoesTuristicas'
      :key='`atracaoTuristica${indice}`'
      :atracaoTuristica='atracaoTuristica'/>
</template>
