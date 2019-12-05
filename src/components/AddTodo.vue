<template>
    <div>
        <input type="text" v-model="todo"  placeholder="Add Todo" >
        <input type="submit" v-on:click="addTodo" value="AddTodo">
    </div>
</template>
<script>
export default {
    name:'AddTodo',
    methods:{
        addTodo(){
            if(this.todo.length>0){
                
                this.$emit("add-todo",this.todo);
            }
            this.todo ="";
        }
    },
    data(){
        return {
            todo:""
        }
    }
}
</script>
<style scoped>
    input{
        padding: 1%;
    }
</style>