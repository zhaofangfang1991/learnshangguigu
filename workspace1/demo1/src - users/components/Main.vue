<template>
    <h2 v-if="firstView">请输入用户名搜索</h2>  
    <h2 v-else-if="loading">loading</h2>
    <h2 v-else-if="errorMsg">{{errorMsg}}</h2>
    
    <div v-else class="row">
      <div class="card" v-for="(user, index) in users" :key="index">
        <a :href="user.home_addr" target="_blank">
          <img :src="user.avadar_addr" style='width: 100px'/>
        </a>
        <p class="card-text">{{user.name}}</p>
      </div>
    </div>
</template>

<script>
import pubSub from "pubsub-js"
import axios from "axios"
export default {
    data () {
        return {
            firstView: true,
            loading:false,
            errorMsg:'',
            users: [], //[{}]
        }
    },
    mounted() {
        pubSub.subscribe("searchName", (msg, searchName) => {
            // ajax
            const url = `https://api.github.com/search/users?q=${searchName}`

            // 状态2 请求中
            this.firstView = false
            this.loading = true
            this.users = []

            axios.get(url).then(response => {
                // 状态3 请求成功
                this.loading = false
                this.users = response.data.items.map(item => ({
                    home_addr: item.html_url,
                    avadar_addr: item.avatar_url,
                    name: item.login
                }))
            }).catch(error => {
                this.loading = false
                this.errorMsg = '请求错误';
                alert('请求错误')
            })
        })
    }
    
}
</script>

<style scoped>
.card {
  float: left;
  width: 33.333%;
  padding: .75rem;
  margin-bottom: 2rem;
  border: 1px solid #efefef;
  text-align: center;
}

.card > img {
  margin-bottom: .75rem;
  border-radius: 100px;
}

.card-text {
  font-size: 85%;
}

</style>