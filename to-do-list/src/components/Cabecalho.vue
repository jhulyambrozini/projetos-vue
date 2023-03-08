
<template>
    <header class="p-5 mb-4 mt-4 text-white">
        <h1>Minhas tarefas</h1>
        <p>Você possui {{ props.tarefasPendentes }} tarefas pendentes</p>
    </header>
</template>

<script setup>
   const props = defineProps(['tarefasPendentes'])
</script>