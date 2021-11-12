<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header :addTodo="addTodo"/>
      <List :todolists="todolists" :delTodo="delTodo"/>
      <Footer/>
    </div>
  </div>
</template>

<script>
import Footer from './components/footer.vue';
import Header from './components/header.vue';
import List from './components/list.vue';
export default {
    data() {
        return {
            todolists: [
                {
                    content: '背英语单词',
                    status: true
                },
                {
                    content: '锻炼身体',
                    status: false
                },
                {
                    content: '泡脚',
                    status: false
                },
            ]
        }
    },
    components: {Header, List, Footer},
    methods: {
        addTodo(todoObject) {
            this.todolists.unshift(todoObject)
        },
        delTodo(index) {
            this.todolists.splice(index, 1)
        }
    }
    
}
</script>


<style scoped>
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
