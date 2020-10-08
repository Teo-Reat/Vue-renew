<template>
  <li
      class="todo__item"
      :class="{done: todo.completed}"
      @click.prevent.right="$emit('remove', todo.id)"
      @click="todo.completed = !todo.completed">
    <span class="todo__number">{{ index + 1 }}: </span>
    <span class="todo__body">{{ todo.title }}: </span>
    <label class="todo__status">
      <input class="todo__checkbox" type="checkbox" v-model="todo.completed">
    </label>
  </li>
</template>

<script>
export default {
  name: "ToDoListItem",
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>
.done {
  background: lightgreen;
}
</style>
