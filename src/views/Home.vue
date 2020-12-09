<template>
  <div class="home">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" v-on:update-todo="updateTodo"/>
  </div>
</template>

<script>
import Todos from './../components/Todos';
import AddTodo from './../components/AddTodo';
import axios from 'axios';
 
export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [

      ]
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => {console.log(res); this.todos = this.todos.filter(todo => todo.id !== id)})
      .catch(err => console.log(err));
    },

    updateTodo(id) {
      this.todos.forEach(todo => {
        if(todo.id == id)
          todo.completed = !todo.completed;
      })
    },

    addTodo(todo){
      const {title, completed} = todo
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
          .then(res => this.todos = res.data)
          .catch(err => console.log(err));
  }
}
</script>

<style>
.btn{
  background: #2D2D2D;
  border: none;
  display: inline-block;
  padding: 7px 20px;
  color: white;
  cursor: pointer;
}

.btn:hover{
  background: #1E1E1E;
}
</style>
