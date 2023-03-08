
<template>
  <div class="container rounded-4 bg-light shadow">
    <header class="p-5 mb-4 mt-4">
      <h1>Minhas tarefas</h1>
      <p>Você possui {{ pegaTarefasPendentes().length }} tarefas pendentes</p>
    </header>

  <form @submit.prevent="cadastraTarefa">
    <div class="row">
      <div class="col">
        <input :value="estado.tarefaTemp" @change="evento => estado.tarefaTemp = evento.target.value" type="text" placeholder="Digite aqui a tarefa" class="form-control" required>
      </div>
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
      <div class="col-md-2">
        <select class="form-control" @change="evento => estado.filtro = evento.target.value">
          <option value="todas">Todas tarefas</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="tarefa in pegaTarefasFiltradas()">
      <input  @change="evento => tarefa.finalizada = evento.target.checked" type="checkbox" :checked="tarefa.finalizada" :id="tarefa.titulo">
      <label :class="{ done: tarefa.finalizada}" :for="tarefa.titulo" class="ms-3">{{ tarefa.titulo }}</label>
    </li>
  </ul>
  
  </div>
</template>

<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    filtro: 'todas',
    tarefaTemp: '',
    tarefas: [
      {
        titulo: 'estudar html',
        finalizada: true
      },
      {
        titulo: 'passear com o cachorro',
        finalizada: false
      }
    ]
  })

  const pegaTarefasPendentes = () => {
   return estado.tarefas.filter(tarefa => !tarefa.finalizada)
  }

  const pegaTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
  }

  const pegaTarefasFiltradas = () => {
    const { filtro } = estado

    switch (filtro){
      case 'pendentes':
        return pegaTarefasPendentes()
      case 'finalizadas':
        return pegaTarefasFinalizadas()
      default:
        return estado.tarefas
    }
  }

  const cadastraTarefa = () => {
    const tarefaNova = {
      titulo: estado.tarefaTemp,
      finalizada: false
    }

    estado.tarefas.push(tarefaNova)
    estado.tarefaTemp = ''
  }
</script>

<style scoped>

.done {
  text-decoration: line-through;
}
</style>


