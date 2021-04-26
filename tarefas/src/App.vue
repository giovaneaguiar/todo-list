<template>
  <div id="app">
    <!-- Título -->
    <h1>Tarefas</h1>
    <!-- @taskAdded="addTask" serve para monitorar quando o evento acontecer,
    chamar o método -->
    <New-Task @taskAdded="addTask"></New-Task>
    <TaskGrid :tasks="tasks"></TaskGrid>
    
  </div>
</template>

<script>
import TaskGrid from "./components/TaskGrid.vue";
import NewTask from "./components/NewTask";
export default {
  components: {
    TaskGrid, NewTask
  },
  data() {
    return {
      tasks: [
        // Passar esses arrays para o componente
        { name: "Lavar a louça", pending: false },
        { name: "Comprar", pending: true },
      ],
    };
  },
  
  methods: {
    
    addTask(task){
      // Cria consts para saber se a task que vai ser adicionada existe ou não na lista.
      const sameName = t => t.name === task.name
      const reallyNew = this.tasks.filter(sameName).length == 0
      if(reallyNew) {
        // Se for realmente novo, inclui no array, se não, ignora.
        this.tasks.push({name: task.name,
        pending: task.pending || true})

      }
      
    }
  }
};
</script>

<style>
/* Estiliza o fundo da aplicação 
   Utiliza degradê com o linear-gradient
*/
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(93, 71, 139), rgb(85, 26, 139));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
