<template>
    <ul class="todo-main">
        <Item v-for="(todolist, index) in todolists" :key="index" :todolist="todolist" :index="index" :delTodo="delTodo"/>
    </ul>
</template>

<script>
import Item from './item.vue'
export default {
    props: {
        "todolists": Array,
        "delTodo": Function
    },
    components:{Item}
}
</script>


<style scoped>
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
