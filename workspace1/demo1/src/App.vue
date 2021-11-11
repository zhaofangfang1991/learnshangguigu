<template>
    <div>
        <header class="site-header jumbotron">
        <div class="container">
            <div class="row">
            <div class="col-xs-12">
                <h1>请发表对自己的规划</h1>
            </div>
            </div>
        </div>
        </header>
        <div class="container">
            <Add :addComments="addComments"/>
            <List :comments="comments" :deleteComments="deleteComments"/>
        </div>
    </div>
</template>

<script>
import Add from './components/Add.vue'
import List from './components/List.vue'

export default {
    data() {
        return {
            comments: [
                {
                    name: 'Bob',
                    content: '我是Bob，我来了'
                },
                {
                    name: 'Eob',
                    content: '我是Eob，我来学vue了'
                },
                {
                    name: 'Xob',
                    content: '我是Xob，我要年底换工作。全栈+算法，加油！'
                },
            ]
        }
    },
    components: {
        Add, List
    },
    methods: {
        addComments(comment) {
            this.comments.unshift(comment)
        },

        deleteComments(index) {
            this.comments.splice(index, 1)
        }
    }
}
</script>

<style scoped>

</style>
