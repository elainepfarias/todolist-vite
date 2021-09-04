<template>
  <h1 class="mt-32 text-center text-4xl font-bold text-gray-600">{{ titulo }}</h1>
  <div class="container p-10 bg-blue-400 text-blue w-4/5 md:w-1/2 lg:w-1/4 mx-auto mt-10 rounded">
    <app-input>
      <input
        class="outline-none"
        v-model="tarefa.descricao"
        type="text"
        placeholder="Descrição da tarefa"
      />
    </app-input>
    <app-btn class="mt-5 mx-auto" @click="adicionarTarefa">Adicionar</app-btn>
  </div>

  <table border="1">
    <thead class="table-fixed border-collapse border border-blue-600 mx-auto mt-10 w-4/5 md:w-1/2 lg:w-1/4">
      <th class="border border-blue-500 px-10 py-3">Concluída</th>
      <th class="border border-blue-500 px-10 py-3">Descrição</th>
    </thead>
    <tbody>
      <tr
        v-for="iterador in tarefas" 
        :key="iterador.descricao"
        :class="{ riscado: iterador.concluida }"
      > 
        <td class="border border-blue-500 px-10 py-3">
          <input type="checkbox" v-model="iterador.concluida" />
        </td>
        <td>{{ iterador.descricao }}</td>
      </tr>
    </tbody>
  </table>
</template>
<script setup>
import AppBtn from "./components/AppBtn.vue";
import AppInput from "./components/AppInput.vue";

import { reactive, ref } from "vue"
//Composition API
const titulo = ref("Todolist")  // valores literais
const tarefas = reactive([]) //lista de tarefas adicionadas  //reactive quando temos objetos
const tarefa = reactive({ // objeto que tem descrição e concluida
  descricao: "",
  concluida: false
})
function adicionarTarefa() {

  tarefas.push(Object.assign({}, tarefa));

}
function remover(indice) {
  tarefas.splice(indice, 1) //por ser vetor podemos utilizar o splice 

}
</script>


<style>
.riscado {
  text-decoration: line-through;
}
</style>
  





