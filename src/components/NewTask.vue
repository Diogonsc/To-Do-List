<template>
  <div class="new-task">
      <input v-model="name" @keydown.enter="add" type="text" class="form-element" placeholder="Nova tarefa?">
      <button class="form-element" @click="add">+</button>
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
      this.$emit("taskAdded", { name: this.name });
      this.name = ""; // para limpar o evento
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
        font-size:2rem;
        border: 1px solid #ffffff;
        padding: 5px 10px 8px;
        color: #fff;
    }

    input.form-element {
        width: 300px;
        background: #FFF2;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }

    button.form-element {
        border-left: none;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
        background-color: rgb(133, 133, 216)
    }

</style>
