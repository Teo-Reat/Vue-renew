<template>
  <form class="todo__add-wrapper" @submit.prevent="createItem">
    <label class="todo__add-label">
      <input class="todo__add-input" type="text" v-model="newItem">
    </label>
    <button class="todo__add-submit" type="submit">Add</button>
  </form>
</template>

<script>
export default {
  name: "ToDoListItemAdd",
  data() {
    return {
      newItem: ''
    }
  },
  methods: {
    createItem() {
      if (this.newItem.trim()) {
        const newItem = {
          id: Date.now(),
          title: this.newItem,
          completed: false
        }

        this.$emit('add-item', newItem)
        this.newItem = ''
      }
    }
  }
}
</script>

<style scoped>

</style>
