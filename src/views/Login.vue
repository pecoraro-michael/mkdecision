<template>
  <div class="login">
    <div class="flex h-screen items-center">
      <!-- login -->
      <div
        class="w-full lg:w-1/2 ml-auto mr-auto bg-white lg:rounded-lg p-10 shadow-md"
        v-if="view === 'login'"
      >
        <div class="text-lg text-gray-700 uppercase font-semibold pb-12">Login</div>
        <div class="flex flex-wrap -mx-3 mb-2">
          <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="username"
            >Username</label>
            <input
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              id="username"
              type="text"
            />
          </div>
          <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="password"
            >Password</label>
            <input
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              id="password"
              type="password"
            />
          </div>
        </div>
        <div class="inline-flex pt-4">
          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded mr-4"
            @click="login('/form')"
          >Sign in</button>
          <!-- <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded"
            @click="login('/form')"
          >Login with Facebook</button>-->
        </div>
        <div class="pt-4">
          <div class="text-sm underline cursor-pointer" @click="changeView('create')">Create account</div>
        </div>
      </div>
      <!-- create account -->
      <div
        class="w-full lg:w-1/2 ml-auto mr-auto bg-white lg:rounded-lg p-10 shadow-md"
        v-if="view === 'create'"
      >
        <div class="text-lg text-gray-700 uppercase font-semibold pb-12">Create an account</div>
        <div class>
          <div class="mb-4">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="username"
            >Email</label>
            <input
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              id="username"
              type="text"
            />
          </div>
          <div class="mb-4">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="username"
            >Password</label>
            <input
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              id="username"
              type="text"
            />
          </div>
          <div class="mb-4">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="username"
            >Confirm password</label>
            <input
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              id="username"
              type="text"
            />
          </div>
        </div>
        <div class="inline-flex pt-4">
          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded mr-4"
            @click="login('/form')"
          >Create Account</button>
        </div>
        <div class="pt-4">
          <div class="text-sm underline cursor-pointer" @click="changeView('login')">Cancel</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import enterCredentials from "@/components/enterCredentials.vue";
import createAccount from "@/components/createAccount.vue";

export default {
  components: {
    enterCredentials,
    createAccount
  },
  data: function() {
    return {
      view: "login",
      isActiveMobile: false
    };
  },
  methods: {
    login: function(param) {
      this.view = param;
      this.$router.push({ path: param });
    },
    changeView: function(param) {
      this.view = param;
    }
  }
};
</script>
