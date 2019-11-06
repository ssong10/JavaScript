<template>
    <div class="todo-list">
      <h2>{{ category }}</h2>
      <input v-model="newTodo">
      <button @click="addTodo">추가</button>
      <li v-for="todo in todos" :key="todo.id">
        {{todo.content}}
        <button @click="removeTodo(todo.id)">x</button>
      </li>
    </div>
</template>

<script>
export default {
      props: {
        category: String,
        required: true
      }, // 하위 컴포넌트로 데이터 전송
      data: function () {
        return {
          todos: [],
          newTodo: ''
        }
      },
      methods: {
        addTodo(todos) {
          this.todos.push({
            id: new Date(),
            content: this.newTodo
          })
          this.newTodo = ''
        },
        removeTodo(id) {
          this.todos = this.todos.filter(todo => {
            return todo.id != id
          })
        }
      }
}
</script>

<style lang="">
/* li {
    color:blue;
} */
</style>