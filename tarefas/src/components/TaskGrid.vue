<template>
  <div class="task-grid">
    <!-- v-if: se tiver alguma task -->
    <template v-if="tasks.length">
      <!-- faz um for para mostrar dentro de cada uma das divs o nome das tasks -->
      <!-- :key="task.name" serve para não aceitar duas tasks com o mesmo nome -->
      <!-- :task="task" serve para passar o valor como um objeto, e não como string -->
      <Task v-for="(task, i) in tasks" :key="task.name" 
      :task="task"
      @taskDeleted="$emit('taskDeleted', i)" 
      @taskStateChanged="$emit('taskStateChanged', i)"
      ></Task>
    </template>
    <!-- se não tiver task alguma, imprime a mensagem -->
    <p v-else class="no-task">Sua vida está em dia :)</p>
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
.task-grid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  /* flex-wrap: wrap --- colocar em linha */
}

.task-grid .task {
  margin: 10px;
}

/* css do texto quando não tiver tarefas na tela. */
.no-task {
  color: #aaa;
  font-size: 1.7rem;
}
</style>