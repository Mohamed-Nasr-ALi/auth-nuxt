<template>
<div>
  users are only show for auth user <br>
  user name: {{ $auth.user.name }},<br>
  user token: {{ $auth.strategy.token.get() }} <br>
  <button class="bg-red-400 text-white border-2 rounded-2xl p-4"  @click="logout">logout</button>
</div>
</template>

<script>
export default {
  name: "users",
  methods:{
   async  logout() {
     await this.$auth.logout()
     await this.$auth.strategy.token.reset()
   }
  }
}
</script>

<style scoped>

</style>
