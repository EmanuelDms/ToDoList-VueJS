<template>
  <!-- Container HTML que a aplicação estará inserida -->
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <FormToDo v-on:add-todo="addComment"></FormToDo>
    <div class="list-group">
      <p v-if="comments.length <= 0">Sem Comentários...</p>
      <div
        class="list-group-item"
        v-for="(comment, index) in allComments"
        v-bind:key="index"
      >
        <span class="comment__author"
          >Autor: <strong>{{ comment.name }}</strong></span
        >
        <p>{{ comment.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)"
            >Excluir</a
          >
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormToDo from "./FormToDo";
export default {
  components: {
    FormToDo,
  },
  /* função que é propriedade de um objeto */
  data() {
    /* Tudo estará disponibilizado no template */
    return {
      comments: [],
    };
  },
  /* Métodos que são disponibilizados para os templates através das diretivas */
  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        name: comment.name.trim() === "" ? "Anônimo" : comment.name,
      }));
    },
  },
  watch: {
    comments(val) {
      console.log(val);
    },
  },
};
</script>

      