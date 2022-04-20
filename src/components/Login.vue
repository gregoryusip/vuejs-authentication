<template>
  <form @submit.prevent="handleSubmit">
    <h3>Login</h3>

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

    <button class="btn btn-primary btn-block">Login</button>
  </form>
</template>

<script>
import axios from "axios";

export default {
  name: "Login",

  data() {
    return {
      email: "",
      password: "",
    };
  },

  methods: {
    async handleSubmit() {
      const response = await axios.post("login", {
        email: this.email,
        password: this.password,
      });

      localStorage.setItem("token", response.data.token);

      // this.$store.dispatch("user", response.data.user);

      this.$router.push("/");
    },
  },
};
</script>
