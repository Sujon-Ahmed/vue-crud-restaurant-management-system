<template>
  <section class="hero-header">
    <div class="signin-card">
      <a href="#"
        ><router-link to="/"
          ><img
            class="logo"
            src="../assets/restro-logo.png"
            alt="logo" /></router-link
      ></a>
      <h3 class="signin-heading">login account</h3>
      <input
        type="email"
        name="email"
        id="email"
        v-model="email"
        placeholder="Enter Email"
        autocomplete="off"
      />
      <input
        type="password"
        name="password"
        id="password"
        v-model="password"
        placeholder="Enter Password"
        autocomplete="off"
      />
      <button @click="signIn" id="submitBtn" type="submit">sign in</button>

      <p class="register-here">
        Create a new account?
        <router-link to="/sign-up">register here</router-link>
      </p>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  name: "SignIn",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async signIn() {
      if (this.email != "" && this.password != "") {
        let result = await axios.get(
          `http://localhost:3000/users?email=${this.email}&password=${this.password}`
        );

        if (result.status == 200 && result.data.length > 0) {
          localStorage.setItem("user-info", JSON.stringify(result.data[0]));
          this.$router.push({ name: "Home" });
        } else {
          alert("Something went wrong!");
        }
      } else {
        alert("All Feild Are Required!");
      }
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>

<style scoped></style>
