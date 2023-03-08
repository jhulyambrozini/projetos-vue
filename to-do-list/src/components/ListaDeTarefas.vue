<template>
    <ul class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" type="checkbox"
                :checked="tarefa.finalizada" :id="tarefa.titulo">
            <label :class="{ done: tarefa.finalizada }" :for="tarefa.titulo" class="ms-3">{{ tarefa.titulo }}</label>
        </li>
    </ul>
</template>

<script setup>

const props = defineProps(['tarefas'])

</script>

<style scoped>

.done {
  text-decoration: line-through;
}
</style>
