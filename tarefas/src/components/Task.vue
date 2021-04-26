<template>
  <div class="task">
    <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
    props: {
        task: {
            type: Object, required: true
        }
    },
    computed: {
        stateClass(){
            //função para ajudar a saber se uma tarefa está pendente ou não.
        }
    }
};
</script>

<style>
</style>