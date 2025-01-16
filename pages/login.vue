<template>
  <section class="py-[50px] flex flex-col items-center justify-center px-4">
    <img src="/assets/svgs/logo-type.svg" alt="" />
    <div class="text-[32px] font-semibold text-dark mt-[70px]">Sign In</div>
    <p class="mt-4 text-base leading-7 text-center mb-[50px] text-grey">
      Manage your employees to achieve <br />
      a bigger goals for your company
    </p>
    <form class="w-full card" @submit.prevent="userLogin">
      <div class="form-group">
        <label for="" class="text-grey">Email Address</label>
        <input type="email" class="input-field" v-model="login.email" />
      </div>
      <div class="form-group">
        <label for="" class="text-grey">Password</label>
        <input type="password" class="input-field" v-model="login.password" />
      </div>
      <button type="submit" class="w-full btn btn-primary mt-[14px]">
            Sign In
        </button>
    </form>
    <!-- Registration link section -->
  <div class="flex gap-2 items-center justify-center mt-6">
    <span class="text-grey">Don't have an account?</span>
    <NuxtLink to="/register" class="text-primary font-medium hover:underline">
      Register
    </NuxtLink>
  </div>
  </section>
</template>

<script>
export default {
  auth: 'guest',
  data() {
    return {
      login: {
        email: '',
        password: ''
      },
      registerPath: '/register'
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>
