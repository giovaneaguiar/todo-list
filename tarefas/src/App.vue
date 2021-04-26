<template>
  <div id="app">
    <!-- Título -->
    <h1>Tarefas</h1>
    <TaskGrid :tasks="tasks"></TaskGrid>
  </div>
</template>

<script>
import TaskGrid from "./components/TaskGrid.vue";
export default {
  components: {
    TaskGrid,
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
};
</script>

<style>
/* Estiliza o fundo da aplicação 
   Utiliza degradê com o linear-gradient
*/
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(71, 60, 139), rgb(72, 118, 255));
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
