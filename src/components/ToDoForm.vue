<template>
  <form @submit.prevent="onSubmit" >
      <label for="new-todo-input" >
          What you want to ToDo?
      </label>
      <input type="text" id="new-todo-input" name="new-todo" autocomplete="off"
        v-model.trim.lazy="label" >
      <button type="submit" >
          Add
      </button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            label: "",
        }
    },
    methods: {
        onSubmit() {
            if(this.label === "") {
                return;
            }
            this.$emit('todo-added', this.label);
            this.label = "";
        }
    }
}
</script>

<style>

</style>