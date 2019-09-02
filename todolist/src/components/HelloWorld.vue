<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Jquery To Do List</h2>
    <h3>Simple Todo List with adding and filter by diff status.</h3>
      <p>
        <label for="new-todo">Add a todo</label><input id="new-todo" v-model="newTodoText"><button>add</button>
      </p>
      <ul>
    <li
      v-for="(todo, index) in todos"
      v-bind:key="todo.id"
      v-bind:title="todo.title"
      v-on:remove="todos.splice(index, 1)"
    ><input type="checkbox" v-model="toggle">
{{todo.title}}</li>
  </ul>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
       newTodoText: '',
       todos:[
         {
        id: 1,
        title: 'Do the dishes',
      },
      {
        id: 2,
        title: 'Take out the trash',
      },
      {
        id: 3,
        title: 'Mow the lawn'
      }
       ],
         nextTodoId: 4
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

</style>
