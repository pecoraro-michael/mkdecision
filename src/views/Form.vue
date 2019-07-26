<template>
  <div class="mkdecision">
    <div class="flex h-screen items-center">
      <div class="w-full lg:w-1/2 ml-auto mr-auto lg:rounded-lg p-12 bg-white">
        <div class="font-semibold text-2xl pb-10">Enter your information to send a message.</div>
        <div class="pb-10 text-red-500" v-if="errors.length">
          <b>Please correct the following error(s):</b>
          <ul>
            <li v-for="(error, index) in errors" :key="index">{{ error }}</li>
          </ul>
        </div>
        <form id="mkdecision" @submit.prevent="handleSubmit">
          <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="fullName">Full Name</label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              v-model="fullName"
              id="fullName"
              type="text"
            />
          </div>
          <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="email">Email Address</label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="username"
              type="email"
              v-model="email"
            />
          </div>
          <div class="mb-6">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="message">Message</label>
            <textarea
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="username"
              type="email"
              v-model="message"
            />
          </div>
          <div class="flex items-center justify-center">
            <button
              type="submit"
              class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded"
            >Submit</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "mkdecision",
  data: function() {
    return {
      fullName: null,
      email: null,
      message: null,
      errors: []
    };
  },
  methods: {
    validateForm: function() {
      if (this.fullName && this.email && this.message) {
        return true;
      }

      this.errors = [];

      if (!this.fullName) {
        this.errors.push("A name is required.");
      }
      if (!this.email) {
        this.errors.push("An email address is required.");
      }
      if (!this.message) {
        this.errors.push("A message is required.");
      }
    },
    handleSubmit: function() {
      this.validateForm();
      if (this.validateForm() === true) {
        axios({
          method: "post",
          url:
            "https://q6vw0wfe70.execute-api.us-east-2.amazonaws.com/01/submission",
          dataType: "json",
          crossDomain: "true",
          data: {
            fullName: this.fullName,
            email: this.email,
            message: this.message
          },
          config: {
            headers: { "Content-Type": "application/json;charset=utf-8" }
          }
        })
          .then(function(response) {
            //handle success
            console.log(response);
          })
          .catch(function(response) {
            //handle error
            console.log(response);
          });
        this.fullName = "";
        this.email = "";
        this.message = "";
      } else {
        console.log("failed validation");
      }
    }
  }
};
</script>
