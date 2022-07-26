<template>
  <div>
    <form @submit.prevent="userLogin">
      <div class="my-3.5">
        <label>Username</label>
        <input class="border-2" type="email" v-model="login.username" />
      </div>
      <div class="my-3.5">
        <label>Password</label>
        <input class="border-2"  type="text" v-model="login.password" />
      </div>
      <div class="my-3.5">
        <label>Remember</label>
        <input class="border-2"  type="checkbox" v-model="login.remember" />
      </div>
      <button class="inline-flex items-center px-4 py-2 font-semibold leading-6 text-sm shadow rounded-md text-white bg-indigo-500  transition ease-in-out duration-150 " :class="{'cursor-not-allowed':loading,'hover:bg-indigo-400':loading}" :disabled="loading">
        <svg v-if="loading" class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
          <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
          <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
        </svg>
        submit
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading:false,
      login: {
        username: '',
        password: '',
        remember:false
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        this.loading=true
        let response = await this.$auth.loginWith('laravelSanctum', { data: this.login })
        console.log(response)
        this.loading=false
      } catch (err) {
        console.log(err)
        this.loading=false
      }
    }
  }
}
</script>
