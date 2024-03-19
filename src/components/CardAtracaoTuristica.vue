<script setup>
defineProps(['atracaoTuristica'])
</script>
<template>
  <section>
    <h2> {{ atracaoTuristica.nome }}</h2>
    <p class='descricaoAtracao'>{{ atracaoTuristica.descricao }}</p>
    <p class='footerCardAtracao'>{{ atracaoTuristica.visitacao }}</p>
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
</style>