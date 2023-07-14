<template>
  <section class="hero-header">
    <div class="signup-card">
      <a href="#"
        ><router-link to="/"
          ><img
            class="logo"
            src="../assets/restro-logo.png"
            alt="logo" /></router-link
      ></a>
      <h3 class="signup-heading">create account</h3>
      <input
        type="text"
        name="name"
        id="name"
        v-model="name"
        placeholder="Enter Name"
        autocomplete="off"
      />
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
      <button @click="signUp" id="submitBtn" type="submit">sign up</button>

      <p class="login-here">
        Have already an account?
        <router-link to="/sign-in">login here</router-link>
      </p>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      if (this.name != "" && this.email != "" && this.password != "") {
        let result = await axios.post("http://localhost:3000/users", {
          name: this.name,
          email: this.email,
          password: this.password,
        });

        if (result.status == 201) {
          localStorage.setItem("user-info", JSON.stringify(result.data));
          this.$router.push({ name: "Home" });
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
