<template>
    <div  id="Todos">
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoVue v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"></TodoVue>
        </div>
        
    </div>
</template>
 
<script>
import TodoVue from './TodoVue';
export default {
    name:"Todos",
    props:["todos"],
    components:{
        TodoVue
    }
}
</script>
<style scoped>

</style>