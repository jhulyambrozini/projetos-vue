
<template>
  <div class="container rounded-4 bg-black shadow pb-4">
    <Cabecalho
    :tarefas-pendentes="pegaTarefasPendentes().length"
    />
    <Formulario
    :tarefa-temp="estado.tarefaTemp"
    :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value"
    :cadastra-tarefa="cadastraTarefa"
    :trocar-filtro="evento => estado.filtro = evento.target.value"
    />
    <ListaDeTarefas
    :tarefas="pegaTarefasFiltradas()"
    />
  </div>
</template>

<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue'
  import Formulario from './components/Formulario.vue'
  import ListaDeTarefas from './components/ListaDeTarefas.vue'


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

