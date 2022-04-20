<template>
  <form @submit.prevent="handleSubmit">
    <h3>Register</h3>

    <div class="form-group mb-3">
      <label for="first_name" class="mb-2">First Name</label>
      <input
        type="text"
        class="form-control"
        v-model="first_name"
        placeholder="First Name"
      />
    </div>

    <div class="form-group mb-3">
      <label for="last_name" class="mb-2">Last Name</label>
      <input
        type="text"
        class="form-control"
        v-model="last_name"
        placeholder="Last Name"
      />
    </div>

    <div class="form-group mb-3">
      <label for="email" class="mb-2">Email</label>
      <input
        type="email"
        class="form-control"
        v-model="email"
        placeholder="Email"
      />
    </div>

    <div class="form-group mb-5">
      <label for="password" class="mb-2">Password</label>
      <input
        type="password"
        class="form-control"
        v-model="password"
        placeholder="Password"
      />
    </div>

    <button class="btn btn-primary btn-block">Sign Up</button>
  </form>
</template>

<script>
import axios from "axios";

export default {
  name: "Register",

  data() {
    return {
      first_name: "",
      last_name: "",
      email: "",
      password: "",
    };
  },

  methods: {
    async handleSubmit() {
      const response = await axios.post("register", {
        first_name: this.first_name,
        last_name: this.last_name,
        email: this.email,
        password: this.password,
      });

      console.log(response);
      this.$router.push("/login");
    },
  },
};
</script>
