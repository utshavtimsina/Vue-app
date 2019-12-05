<template>
    <div class="TodoVue">
      
       <p v-bind:class="{'is-Compleated':todo.completed}"> 
           <input type="checkbox" v-on:change="checkBoxClicked">
            {{todo.title}} 
            <button class="btn" v-on:click="buttonClicked"><i class="fa fa-trash"></i></button></p>
       
       
    </div>
</template>
<script>
export default {
    name:"TodoVue",
    props:["todo"],
    methods:{
        checkBoxClicked(){
           this.todo.completed = !this.todo.completed;
        },
        buttonClicked(){
           // alert("");
            this.$emit("del-todo",this.todo.id);
        }
    },
}
</script>

<style scoped>
.TodoVue{
    background-color: black;
    color: white;
}
p{  
    text-align: center;
    padding: 1%;
    margin: 0%;
}
.is-Compleated{
    text-decoration: line-through;
}
button{
    margin-left: 20px;
}
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css";
</style>
