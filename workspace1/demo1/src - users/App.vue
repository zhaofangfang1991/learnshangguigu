<template>
  <div class="container">
    <Search/>
    <user-main/>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import Search from './components/Search.vue'
export default {
  data() {
    return {

    }
  },
  components:{
      Search,
      UserMain: Main
  }
    
}
</script>


<style scoped>
</style>
