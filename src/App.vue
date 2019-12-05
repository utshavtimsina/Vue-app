<template>
  <div id="app" > 
  <Header ></Header>
  <hr>
  <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo"> </Todo>
  <AddTodo v-on:add-todo="addTodo"></AddTodo>
</div>
</template>

<script>
import Header from './components/Header.vue';
import Todo from './components/Todo.vue';
import AddTodo from './components/AddTodo.vue';
import axios from 'axios';
export default{
  name: 'app',
  components:{
    Header,
    Todo,
    AddTodo,
    
  },
  methods:{
    deleteTodo(id){
    //alert(id);
    axios
    .delete("https://jsonplaceholder.typicode.com/todos/"+id)
    .then(res => {
      //alert(JSON.stringify(res.data));
      console.log(res);
      this.todos = this.todos.filter(todo => todo.id != id)
      });
      
    },
    addTodo(todo){
      
      axios
        .post("https://jsonplaceholder.typicode.com/todos",{
           "title":""+todo,
            "completed":false
        })
        .then(res =>{
          this.todos.push(res.data);
        })
        .catch();
      //this.todos.push(addTodo);
    }
  },
  data(){
   
       return {
        
         todos:[]
       }

  },
  created(){
    axios
        .get('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(res =>this.todos = res.data)
        .catch();
        
  }
   
  
}
</script>

<style >
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
Header{
  padding: 20%;
  margin: 10%;
}
</style>
