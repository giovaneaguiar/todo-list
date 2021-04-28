<template>
  <div id="app">
    <!-- Título -->
    <h1>Tarefas</h1>
    <TaskProgress :progress="progress"></TaskProgress>
    <!-- @taskAdded="addTask" serve para monitorar quando o evento acontecer,
    chamar o método -->
    <New-Task @taskAdded="addTask"></New-Task>
    <TaskGrid
      @taskDeleted="deleteTask"
      @taskStateChanged="toggleState"
      :tasks="tasks"
    ></TaskGrid>
  </div>
</template>

<script>
import TaskGrid from "./components/TaskGrid.vue";
import NewTask from "./components/NewTask";
import TaskProgress from "./components/TaskProgress";
export default {
  components: {
    TaskGrid,
    NewTask,
    TaskProgress,
  },
  computed: {
    progress() {
      const total = this.tasks.length;
      // total: pega o tamanho do array.
      const done = this.tasks.filter((t) => !t.pending).length;
      // done: função que pega todos que não estão pendentes.
      return Math.round((done / total) * 100) || 0;
      // retorna calculo correto para fazer a barra de porcentagem.
    },
  },
  watch: {
    //monitorar as tasks - sempre que o array mudar, ele chama essa função
    tasks: {
      deep: true,
      //olhar profundamente
      handler() {
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
        //monitorar os elementos em si, para quando atualizar
        //o navegador, continuar as tasks.
      },
    },
  },
  data() {
    return {
      tasks: [
        //inicialmente vazios, ou seja, sem tarefas iniciais no projeto.
      ],
    };
  },

  methods: {
    addTask(task) {
      // Cria consts para saber se a task que vai ser adicionada existe ou não na lista.
      const sameName = (t) => t.name === task.name;
      const reallyNew = this.tasks.filter(sameName).length == 0;
      if (reallyNew) {
        // Se for realmente novo, inclui no array, se não, ignora.
        this.tasks.push({ name: task.name, pending: task.pending || true });
      }
    },
    deleteTask(i) {
      this.tasks.splice(i, 1);
      // i: indice do array que quero deletar, ou seja, qual task eu quero
      // 1: numero de tasks que quero deletar, ou seja, 1 task apenas.
    },

    toggleState(i) {
      // se estiver pendente, ele coloca falso
      // se não estiver pendente, ele coloca verdadeiro
      this.tasks[i].pending = !this.tasks[i].pending;
    },
  },
  created() {
    const json = localStorage.getItem("tasks");
    const array = JSON.parse(json);
    if (Array.isArray(array)) {
      //se for um array de fato...
      this.tasks = array;
      //voce seta o valor desse array no this.tasks.
    } else {
      this.tasks = [];
      //se não, utiliza um array vazio.
    }
  },
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
