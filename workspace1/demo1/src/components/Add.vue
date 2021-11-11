<template>
    <div class="col-md-4">
        <form class="form-horizontal">
        <div class="form-group">
            <label>用户名</label>
            <input type="text" class="form-control" placeholder="用户名" v-model="name">
        </div>
        <div class="form-group">
            <label>评论内容</label>
            <textarea class="form-control" rows="6" placeholder="评论内容" v-model="content"></textarea>
        </div>
        <div class="form-group">
            <div class="col-sm-offset-2 col-sm-10">
            <button type="button" class="btn btn-default pull-right" @click="add">提交</button>
            </div>
        </div>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: '',
            content: ''
        }
    },
    props: {
        addComments: {
            type: Function,
            required: true
        }
    },
    methods: {
        add() {
            // 获取数据，判断数据的合法性
            const name = this.name.trim()
            const content = this.content.trim()

            if (!name || !content) {
                alert('name or content must not be blank')
                return
            }

            // 整合数据
            const comment = {
                'name': name,
                'content': content
            }

            // 使用方法
            this.addComments(comment)


        }
    },
}
</script>

<style scoped>

</style>
