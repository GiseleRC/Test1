<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <todoapp msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import todoapp from '@/components/todoapp.vue'

export default {
  name: 'Home',
  components: {
    todoapp
  }
}
</script>

