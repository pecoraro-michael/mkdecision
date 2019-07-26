<template>
  <div class="login">
    <div class="flex h-screen items-center text-center">
      <div class="w-full lg:w-1/2 ml-auto mr-auto bg-white lg:rounded-lg p-20 shadow-md">
        <div class="text-2xl font-semibold pb-12">Login</div>
        <div class="inline-flex">
          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded mr-4"
            @click="login('/form')"
          >Sign in with Google</button>
          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded"
            @click="login('/form')"
          >Login with Facebook</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      view: "",
      isActiveMobile: false
    };
  },
  methods: {
    login: function(param) {
      this.view = param;
      this.$router.push({ path: param });
    }
  }
};
</script>
