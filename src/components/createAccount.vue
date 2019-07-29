<template>
  <div
    class="w-full lg:w-1/2 ml-auto mr-auto bg-white lg:rounded-lg p-20 shadow-md"
    v-if="view = 'login'"
  >
    <div class="text-2xl font-semibold pb-12">Create an account</div>
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
    <div class="pt-4">
      <div class="text-sm underline cursor-pointer" @click="createAccount()">Create an account</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>
