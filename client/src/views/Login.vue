<script>
import { mapActions } from 'pinia'
import { useUserStore } from '../stores/user'

export default {
  data() {
    return {
      data: {}
    }
  },
  methods: {
    ...mapActions(useUserStore, ['login', 'googleSign'])
  }
}
</script>
<template>
  <div class="overflow-hidden lg:flex-row flex-col-reverse flex lg:w-screen lg:h-screen">
    <div class="lg:w-1/2 p-5">
      <RouterLink to="/">
        <p class="text-[20px]">I LIKE IT</p>
      </RouterLink>
      <form @submit.prevent="login(data)" class="h-[85vh] flex items-center justify-center lg:my-0 my-32">
        <div class="lg:mt-14 lg:my-0 lg:max-w-md max-w-md  w-full ">
          <div class="lg:shadow-none shadow p-5 rounded-md">
            <h1 class="font-bold lg:text-3xl text-4xl mb-5 ">Login</h1>
            <div class="space-y-4">
              <div>
                <input v-model="data.email" type="email" class="rounded-md p-3 border shadow w-full outline-none"
                  placeholder="Email" required />
              </div>
              <div>
                <input v-model="data.password" type="password" class="rounded-md p-3 border shadow w-full outline-none"
                  placeholder="Password" required />
              </div>
            </div>

            <button type="submit" class="bg-secondary w-full py-3 text-white rounded-md my-6 disabled:bg-slate-400">
              Login</button>
            <div class="flex mb-5 justify-center w-full items-center">
              <GoogleLogin :callback="googleSign" />
            </div>
            <div class="w-full text-center">
              <h4 class="w-max p-3 -ml-3">
                Don't have an account yet ? <RouterLink to="/register" class="text-sm tracking-wide text-blue-600">
                  Sign Up</RouterLink>
              </h4>
            </div>
          </div>
          <div
            class="text-secondary mt-5 px-8 py-2 buttom-[10px] text-center text-base leading-5 lg:hidden landscape:hidden ">
            <p>we have some awesome fetures for more info</p>

            <button class="border-[#0E8CF2] mt-5 px-8 py-2 border text-[16px] rounded-md">Visit Us</button>
          </div>
        </div>
      </form>
    </div>
    <div class="w-1/2 lg:block hidden bg-[#8FCCFF] p-5">
      <div class="text-secondary text-end text-base leading-5  ">
        <p>we have some awesome fetures</p>
        <p>for more info</p>
      </div>
      <div class="flex items-center justify-center h-[90vh] ">
        <img src="../assets/cook.svg" alt="" class="max-w-md  " />
      </div>
    </div>
  </div>
</template>