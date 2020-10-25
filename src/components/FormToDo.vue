<template>
  <div class="form-todo form-group">
    <p>
      <input
        type="text"
        placeholder="nome"
        name="author"
        class="form-control"
        v-model="name"
      />
    </p>
    <p>
      <textarea
        name="messsage"
        class="form-control"
        v-model="message"
        placeholder="Comentário"
      ></textarea>
    </p>
    <button v-on:click="addComment" type="submit" class="btn btn-primary">
      Comentar
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      /* trim apaga espaços em branco antes e depois */
      if (this.message.trim() == "") return;

      this.$emit("add-todo", {
        name: this.name,
        message: this.message,
      });

      /* altera no model e reflete na view */
      this.name = "";
      this.message = "";
    },
  },
};
</script>

<style>
</style>