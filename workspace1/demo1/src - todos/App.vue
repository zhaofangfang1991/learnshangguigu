<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header :addTodo="addTodo"/>
      <List :todolists="todolists" :delTodo="delTodo"/>
      <Footer :todolists="todolists" :deleteComplatedItem="deleteComplatedItem" :selectAllItem="selectAllItem"/>
    </div>
  </div>
</template>

<script>
import Footer from './components/footer.vue';
import Header from './components/header.vue';
import List from './components/list.vue';
export default {
    data() {
      // content: '背英语单词',
                    // status: true
        return {
            todolists: JSON.parse(window.localStorage.getItem('todo_item') || '[]')
        }
    },
    components: {Header, List, Footer},
    methods: {
        addTodo(todoObject) {
            this.todolists.unshift(todoObject)
        },
        delTodo(index) {
            this.todolists.splice(index, 1)
        },
        deleteComplatedItem() {
          this.todolists = this.todolists.filter(todo => !todo.status)
        },
        selectAllItem(check) {
          this.todolists.forEach(todo => todo.status=check)
        }
    },
    watch: {
      // todolists存缓存，从缓存中取
      todolists: {
        deep: true,
        handler: function(value) {
          // 存缓存
          window.localStorage.setItem('todo_item', JSON.stringify(value))
        }
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
