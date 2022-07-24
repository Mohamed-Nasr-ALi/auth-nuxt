<template>
  <nav class="px-3 text-green-600 m-2.5 pt-3 capitalize pb-3.5">
    <NuxtLink class="p-2.5 border-2 rounded-2xl" to="/">home</NuxtLink>
    <NuxtLink class="p-2.5 border-2 rounded-2xl" to="users">all users</NuxtLink>
    <NuxtLink class="p-2.5 border-2 rounded-2xl" v-if="!$auth.loggedIn" to="login">login</NuxtLink>
  </nav>
</template>

<script>
export default {
  name: "TheHeader"
}
</script>

<style scoped>

</style>
