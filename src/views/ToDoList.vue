<template>
  <div class="todo__wrapper">
    <router-link to="/">Home</router-link>
    <to-do-list-item-add @add-item="addItem"></to-do-list-item-add>
    <loader v-if="loading"></loader>
    <ul class="todo" v-else-if="toDoList.length">
      <to-do-list-item
          v-for="(toDoItem, key) in toDoList"
          :index="key"
          :todo="toDoItem"
          @remove="removeItem">
      </to-do-list-item>
    </ul>
    <div class="todo__empty" v-else>Nothing to view</div>
  </div>
</template>

<script>
import ToDoListItem from "@/components/ToDoListItem";
import ToDoListItemAdd from "@/components/ToDoListItemAdd";
import Loader from "@/components/Loader"

export default {
  name: "ToDoList",
  components: {
    ToDoListItem,
    ToDoListItemAdd,
    Loader
  },
  data() {
    return {
      toDoList: [],
      loading: true
    }
  },

  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(response => response.json())
        .then(json => {
          setTimeout(() => {
            this.toDoList = json
            this.loading = false
          }, 1000)
        })
  },

  methods: {
    removeItem(id) {
      this.toDoList = this.toDoList.filter(t => t.id !== id)
    },
    addItem(newItem) {
      this.toDoList.push(newItem)
    }
  }
}
</script>

<style scoped>

</style>
