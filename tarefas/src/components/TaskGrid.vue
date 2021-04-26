<template>
<div class="task-grid">

    <template>
        <!-- faz um for para mostrar dentro de cada uma das divs o nome das tasks -->
        <!-- :key="task.name" serve para não aceitar duas tasks com o mesmo nome -->
        <div v-for="task in tasks" :key="task.name">{{ task.name }}</div>
    </template>
    
</div>
</template>

<script>
export default {
  //Componente que precisa receber uma lista de tarefas.
  // required: true (significa um atributo obrigatório).
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
</style>