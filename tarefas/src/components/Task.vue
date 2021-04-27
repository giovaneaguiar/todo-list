<template>
  <div 
     @click="$emit('taskStateChanged', task)"
     class="task" :class="stateClass">
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
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
    position: relative;
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

/* Estiliza x quando task pendente */
.pending .close {
  background-color: #b73229;
}

/* Estiliza x quando task concluida */
.done .close {
  background-color: #0a8f08;
}

.close {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 0.9rem;
  font-weight: 600;
  height: 20px;
  width: 20px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
}
</style>
