<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Jquery To Do List</h2>
    <h3>Simple Todo List with adding and filter by diff status.</h3>
      <p>
        <label for="new-todo">Add a todo</label><input id="new-todo" v-model="newTodoText"><button @click="addTodo">add</button>
      </p>
      <ul>
    <li
      v-for="(todo) in todos"
      v-bind:key="todo.id"
      v-bind:title="todo.title">
      <input type="checkbox" id="todo.id" v-model="todo.checked" @change="changeTodo(todo)">
      
    <span v-if="todo.checked==true" class="checked">{{todo.title}}</span>
    <span v-else>{{todo.title}}</span>
    </li>
  </ul>
    <p><button @click="allClick">all</button><button @click="activeTodo">Active</button><button @click="completeTodo">Complete</button></p>

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
       toggle:false,
       todos:[
       
       ],
         nextTodoId: 1,
         todoAll:[]
    }
  },methods:{
    addTodo:function(){
      this.todos.push({id:this.nextTodoId,title:this.newTodoText,checked:false})
      this.todoAll = this.todos;
      this.nextTodoId=this.nextTodoId+1;
    },
    changeTodo:function(option){
     this.todos.forEach(element => {
       if(element.id==option.id){
         var newObj={};
         newObj.id = element.id;
         newObj.title = element.title;
         newObj.checked=!element.checked;
       }
     });
    },
    allClick:function(){
      this.todos = this.todoAll;
    },
    activeTodo:function(){
      var tempObj=[];
      this.todoAll.forEach(element=>{
        if(element.checked==false){
          tempObj.push(element);
        }
      })
      this.todos = tempObj;
    },
    completeTodo:function(){
      var tempObj=[];
      this.todoAll.forEach(element=>{
        if(element.checked==true){
          tempObj.push(element);
        }
      })
      this.todos=tempObj;
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
label{
  margin: 10px;
}
button{
  margin: 10px;
}
ul{
  margin:0 auto;
 display:block;
 padding:0px;
}
.checked{
  text-decoration:line-through;
}
</style>
