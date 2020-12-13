<template>
  <div>
    <router-link to=/>Главная страница</router-link>
    <Todoadd
        @add-todo="Todoadd"
    />
    <hr>
    <!--<Loader v-if="loading" />-->
    <TODOList
      v-bind:todos="todos"
      @remove-task='removeTask'
    />

  </div>
</template>

<script>

import TODOList from '@/components/TODOList'
import Todoadd from '@/components/AddTodo'
export default {
  name: 'App',
  data(){
    return {
      todos: []
    }
    },
    mounted(){
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
        .then(response => response.json())
        .then(json => {this.todos = json})

    },
    methods: {
      removeTask(id) {
           this.todos = this.todos.filter( t => t.id !== id)
        },
      Todoadd(todo) {
        this.todos.push(todo)
      }
  },
  components: {
    TODOList, Todoadd
  }
}
</script>
