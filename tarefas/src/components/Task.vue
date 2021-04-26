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
</style>