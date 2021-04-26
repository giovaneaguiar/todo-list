<template>
  <div class="new-task">
    <!-- Formulário para adicionar uma nova tarefa,
      juntamente com um botão -->

    <input v-model="name" @keydown.enter="add" type="text">
    <button @click="add">+</button>
    <!-- Tanto o click do botão, quanto o enter, chamam o método add() -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
    };
  },
  methods: {
    add() {
      /*  Método para fazer duas coisas: Emitir um evento de que foi adicionado um elemento, quando for apertado
            enter ou o botão '+', mandar para o componente pai (App.vue) de que uma task foi adicionada.
            E também limpar o valor de 'name' para incluir outra tarefa, por exemplo.
            */
           this.$emit('taskAdded', {name: this.name});
           this.name = '';
    },
  },
};
</script>

<style>
</style>