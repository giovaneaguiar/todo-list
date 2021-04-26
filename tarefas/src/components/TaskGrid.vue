<template>
  <div class="task-grid">
    <template>
      <!-- faz um for para mostrar dentro de cada uma das divs o nome das tasks -->
      <!-- :key="task.name" serve para não aceitar duas tasks com o mesmo nome -->
      <!-- :task="task" serve para passar o valor como um objeto, e não como string -->
      <Task v-for="task in tasks" :key="task.name" :task="task"></Task>
    </template>
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  components: { Task },
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