<template>
    <li @mouseenter="enterli(true)" @mouseleave="enterli(false)" :style={background:bgColor}>
        <label>
        <input type="checkbox" v-model="todolist.status" />
        <span>{{todolist.content}}</span>
        </label>
        <button class="btn btn-danger" v-show="isShow" style="display:block" @click="delItem(index)">删除</button>
    </li>
</template>

<script>

export default {
    data() {
        return {
            bgColor: 'white',
            isShow: false
        }
    },
    props: {
        'todolist': Object,
        'index' : Number,
        'delTodo': Function
    },
    methods: {
        enterli(isEnter) {
            if (isEnter) {
                this.bgColor = '#ccc'
                this.isShow = true
            } else {
                this.bgColor = 'white'
                this.isShow = false
            }
        },
        delItem(index) {
            console.log(index);
            // 确认
            if(window.confirm(`确认删除${this.todolist.content}吗？`)) {
                // 删除
                this.delTodo(index)
            }


        }
    }
    
    
}
</script>


<style scoped>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>
