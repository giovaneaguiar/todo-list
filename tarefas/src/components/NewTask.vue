<template>
  <div class="new-task">
    <!-- Formulário para adicionar uma nova tarefa,
      juntamente com um botão -->

    <input
      class="form-element"
      placeholder="Nova tarefa?"
      v-model="name"
      @keydown.enter="add"
      type="text"
    />
    <button class="form-element" @click="add">+</button>
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
      this.$emit("taskAdded", { name: this.name });
      this.name = "";
    },
  },
};
</script>
<style>
.new-task {
  margin: 35px;
}

.form-element {
    outline: none;
    font-size: 2rem;
    border: 1px solid #fff;
    padding: 5px 10px 8px;
    color: #fff;

}

input.form-element {
    width: 500px;
    background-color: #fff2;
    /* bordas apenas no lado esquerdo */
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;

}

button.form-element{
    border-left: none;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
    background-color: #AB82FF;
}
</style>