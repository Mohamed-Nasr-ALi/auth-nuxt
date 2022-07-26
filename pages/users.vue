<template>
<div>
  users are only show for auth user <br>
  user name: {{ $auth.user.name }},<br>
  user token: {{ $auth.strategy.token.get() }} <br>
  <button class="bg-red-400 text-white border-2 rounded-2xl p-4"  @click="logout">logout</button>
  <br>
  <ul>
    <li v-for="user in allUsers" :key="user.id">{{user.name}} -> {{user.email}}</li>
  </ul>
</div>
</template>

<script>
export default {
  mounted() {
    this.getALlUsers()
  },
  name: "users",
  data(){
    return{
      users:[]
    }
  },
  computed:{
    allUsers(){
      return this.users;
    }
  },
  methods:{
    async getALlUsers(){
      const data=await this.$axios.$get('/api/dashboard/profile/all');
      this.users=data.data
    },
   async  logout() {
     await this.$auth.logout()
   }
  }
}
</script>

<style scoped>

</style>
