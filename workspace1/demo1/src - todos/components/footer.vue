<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox" v-model="isAllCheck"/>
        </label>
        <span>
            <span>已完成{{complatedSize}}</span> / 全部{{todolists.length}}
        </span>
        <button class="btn btn-danger" v-show="complatedSize" @click="deleteComplatedItem">清除已完成任务</button>
    </div>
</template>

<script>

export default {
    props:{
        'todolists': Array,
        'deleteComplatedItem': Function,
        'selectAllItem': Function
    },
    
    components: {},
    // 计算属性
    computed: {
        complatedSize () {
            // 已完成数量，是通过todolists的完成状态计算而来的
            return this.todolists.reduce((preTotal, todo) => preTotal + (todo.status?1:0), 0)
        },
        // isAllCheck这个复选框的值，随时在监视其他复选框的状态
        isAllCheck:{
          get () {
            return this.todolists.length === this.complatedSize  && this.complatedSize>0  // 当todo的所有个数和已完成状态的个数相等时，选中
          },
          set(value) {
            // 该复选框选中时，其他的所有复选框选中；不选中时其他的复选框不选中
            this.selectAllItem(value)
          }
        }
    }
    
}
</script>


<style scoped>
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

</style>
