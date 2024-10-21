<template>
  <input type="text" v-model="userName" placeholder="Name">
  <input type="password" v-model="userPass" placeholder="Password">
  <input type="email" v-model="userEmail" placeholder="Email">


</template>

<script>
export default {
  data() {
    return {
      userName: '',
      userPass: '',
      userEmail: ''
    }
  },
  methods: {}
}

</script>


<style scoped>

</style>
