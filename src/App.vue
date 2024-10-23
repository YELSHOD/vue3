<template>
  <input type="text" v-model="userName" placeholder="Name">
  <input type="password" v-model="userPass" placeholder="Password">
  <input type="email" v-model="userEmail" placeholder="Email">
  <p className = "error">{{ error }}</p>
  <button @click="sendData()">Отправить</button>

  <div v-if="users.length == 0" className="user">
    У нас нет пользователей
  </div>

  <div v-else-if="users.length == 1" className="user">
    Users has 1 element
  </div>

  <div v-else className="user">
    Users has more than 1 element
  </div>

  <User v-for="(el,index) in users" :key="index" :user="el" :index = "index" :deleteUser="deleteUser"/>

</template>

<script>
import User from "@/components/User.vue";

export default {
  components:  {User},
  data() {
    return {
      users: [],
      error: '',
      userName: '',
      userPass: '',
      userEmail: ''
    }
  },
  methods: {
    sendData() {
      if (this.userName == '') {
        this.error = 'Имя не введено';
        return;
      }
      else if(this.userEmail == '') {
        this.error = 'Email не введен'
        return;
      }
      else if(this.userPass == '') {
        this.error = 'Пароль не введен'
        return;
      }
      this.error = '';


      this.users.push({
          name: this.userName,
          pass: this.userPass,
          email: this.userEmail
      })
    },

    deleteUser(index) {
          this.users.splice(index, 1);
    }

  }
}

</script>


<style scoped>

</style>
