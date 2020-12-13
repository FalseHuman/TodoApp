<template>
    <div>
        <ul>
            <Todoitem 
              v-for="(todo, i) of todos"
              v-bind:todo="todo"
              v-bind:index="i"
              v-on:remove-task="removeTask"
            />
        </ul>
    </div>
</template>
<script>
import Todoitem from '@/components/Todoitem'
export default {
   props: ['todos'],
   components: {
       Todoitem
   },
   methods:{
       removeTask(id){
           this.$emit('remove-task', id)
       }
   }
}
</script>
<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>