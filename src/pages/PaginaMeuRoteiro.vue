<script setup>
import {inject} from 'vue';

const meuRoteiro = inject('meuRoteiro')

const excluiAtracaoDoRoteiro = (atracaoTuristica) => {
  const indiceAtracao = meuRoteiro.value.indexOf(atracaoTuristica)
  meuRoteiro.value.splice(indiceAtracao, 1)
}
</script>
<template>
  <h1>Meu roteiro</h1>
  <table>
    <thead>
    <tr>
      <th>Ordem</th>
      <th>Nome atração</th>
      <th>Visitacao</th>
      <th></th>
    </tr>
    </thead>
    <tbody>
    <tr v-for='(atracaoRoteiro, indice) in meuRoteiro'
        :key='`atracaoRoteiro${indice}`'>
      <td style='text-align: right; padding: 15px'>
        {{ indice + 1 }}
      </td>
      <td>
        {{ atracaoRoteiro.nome }}
      </td>
      <td>
        {{ atracaoRoteiro.visitacao }}
      </td>
      <td>
        <button @click='() => excluiAtracaoDoRoteiro(atracaoRoteiro)'>
          Excluir
        </button>
      </td>
    </tr>
    </tbody>
    <tfoot>
    <tr>
      <td colspan='4'>
        Total atrações: {{ meuRoteiro.length }}
      </td>
    </tr>
    </tfoot>
  </table>
</template>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  border: 2px solid darkgreen;
  border-radius: 10px;
}

table > thead > tr > th {
  margin: 10px;
  padding: 10px;
  border: 1px solid darkgreen;
}

table > tbody > tr > td {
  margin: 10px;
  padding: 10px;
  border: 1px solid darkgreen;
}

table > tfoot > tr > td {
  text-align: right;
  margin: 10px;
  padding: 10px;
  font-weight: bolder;
  color: #073b4c;
  border: 1px solid darkgreen;
}

button {
  padding: 10px 10px;
  background-color: #c97f57;
  border: none;
  border-radius: 5px;
  font-size: smaller;
  text-align: left;
}
</style>
