<template>
  <body>
    <div id="app">
      <h2>TODO List</h2>
      <form v-on:submit.prevent>
        <input type="text" v-model="newItem">
        <button v-on:click="addItem">Add</button>
      </form>
      <ul>
        <li v-for="todo, index in todos" :key="todo.item">
          <input type="checkbox" v-model=todo.isDone>
          <span v-bind:class="{done: todo.isDone}">
            {{ todo.item }}
          </span>
          <button v-on:click="deleteItem(index)">削除</button>
        </li>
      </ul>
    </div>
  </body>
</template>

<script>
export default {
  data: () => ({
    'newItem': '',
    'todos': []
  }),
  methods: {
    addItem() {
      if (this.newItem==='') return
      let todo = {
        item: this.newItem,
        isDone: false
      }
      this.todos.push(todo)
      this.newItem = ''
    },
    deleteItem(index) {
      console.log(index)
      this.todos.splice(index, 1)
    }
  },
}
</script>

<style scoped>
  li {
    list-style: none;
  }
  .done{
    text-decoration: line-through;
  }
</style>
