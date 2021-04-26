<template>
  <div class="task" :class="stateClass">
    <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
  computed: {
    stateClass() {
      //função para ajudar a saber se uma tarefa está pendente ou não.
      return {
        // se estiver pendente, marcar pendente
        pending: this.task.pending,
        //caso contrário, marcará classe css 'done'
        done: !this.task.pending,
      };
    },
  },
};
</script>
<style>
.task {
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2rem;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    /* user select: o usuário não vai conseguir selecionar o texto */
    display: flex;
    justify-content: center;
    align-items: center;

}

/* Estiliza quando tarefa pendente */
.pending {
    border-left: 12px solid #B73229;
    background-color: #F44336;


}
/* Estiliza quando tarefa concluída */
.done {
    color:#ddd;
    border-left: 12px solid #0A8F08;
    background-color: #4CAF50;
    text-decoration: line-through;
    /* line-through: linha riscando o texto */
}

</style>