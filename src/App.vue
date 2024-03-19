<script setup>
import PaginaHome from '@/pages/PaginaHome.vue';
import PaginaAtracoesTuristicas from '@/pages/PaginaAtracoesTuristicas.vue';
import PaginaMeuRoteiro from '@/pages/PaginaMeuRoteiro.vue';
import {provide, ref} from 'vue';

const paginaSelecionada = ref(0)

const paginas = [
  {titulo: 'Home', componente: PaginaHome},
  {titulo: 'Atrações turísticas', componente: PaginaAtracoesTuristicas},
  {titulo: 'Meu roteiro', componente: PaginaMeuRoteiro},
]

const meuRoteiro = ref([])
provide('meuRoteiro', meuRoteiro)

</script>

<template>
  <header>
    <div class='menuPaginas'>
      <a v-for='(pagina, indicePagina) in paginas' :key='`pagina${indicePagina}`'
      @click='paginaSelecionada = indicePagina'>
        {{ pagina.titulo}}
        <span v-if="indicePagina === 2"> ({{meuRoteiro.length}})</span>
      </a>
    </div>
  </header>
  <main>
    <div>
      <KeepAlive>
        <component :is='paginas[paginaSelecionada].componente' />
      </KeepAlive>
    </div>
  </main>
</template>

<style scoped>
</style>
