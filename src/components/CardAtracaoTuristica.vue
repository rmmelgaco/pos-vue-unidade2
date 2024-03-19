<script setup>
import {inject} from 'vue';

defineProps(['atracaoTuristica'])
const meuRoteiro = inject('meuRoteiro', [])
const emit = defineEmits(['enviar-mensagem'])

const adicionaAtracaoAoRoteiro = (atracaoTuristica) => {
  if (meuRoteiro.value.includes(atracaoTuristica)) {
    emit('enviar-mensagem', 'Atração já adicionada ao meu roteiro.')
  } else {
    meuRoteiro.value.push(atracaoTuristica)
  }
}
</script>
<template>
  <section>
    <h2> {{ atracaoTuristica.nome }}</h2>
    <p class='descricaoAtracao'>{{ atracaoTuristica.descricao }}</p>
    <p class='footerCardAtracao'>{{ atracaoTuristica.visitacao }}</p>
    <button @click='() => adicionaAtracaoAoRoteiro(atracaoTuristica)'>Adicionar ao roteiro</button>
  </section>
</template>

<style scoped>
section {
  margin: 10px;
  padding: 10px;
  border: 1px solid lightgray;
  border-radius: 10px;
  box-shadow: 2px 2px 2px lightgray;
}

section > .descricaoAtracao {
  font-size: 1.2rem;
  text-indent: 2rem;
  text-align: justify;
}

section > .footerCardAtracao {
  text-align: right;
}
section > button {
  padding: 10px 50px;
  background-color: #a7c957;
  border: none;
  border-radius: 5px;
}
</style>