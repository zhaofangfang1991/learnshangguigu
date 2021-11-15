<template>
  <div>
    <div v-if="!address_name">loading...</div>
    <div v-else>这里是地址： <a :href="address">{{address_name}}</a></div>
  </div>
</template>

<script>
import axios from 'axios'
export default {  
  data() {
    return {
      address:'', // 从后台返回数据的地址
      address_name:'' // 从后台返回数据的名称
    }
  },
  mounted() {
    const httpAddr = 'https://api.github.com/search/repositoties?q=vue&sort=starts'

    axios.get(httpAddr).then(response => {
      const result = response.data
      console.log(result);

    }).catch(error => {
      alert('错误分支')
    })
  }

}
</script>


<style scoped>
</style>
