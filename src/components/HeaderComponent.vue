<template>
  <header>
    <div class="container">
      <input type="checkbox" name="check" id="check" />

      <div class="logo-container">
        <h3 class="logo">Brand<span>Name</span></h3>
      </div>

      <div class="nav-btn">
        <div class="nav-links">
          <ul>
            <li class="nav-link" style="--i: 0.6s">
              <router-link to="/home">Home</router-link>
            </li>
            <li class="nav-link" style="--i: 0.6s">
              <router-link to="/add-restaurant">Add Restaurant</router-link>
            </li>
          </ul>
        </div>

        <div class="log-sign" style="--i: 1.8s">
          <a href="#" @click="logout" class="btn solid">Logout</a>
        </div>
      </div>

      <div class="hamburger-menu-container">
        <div class="hamburger-menu">
          <div></div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "WelcomePage" });
    },
  },
};
</script>

<style scoped></style>
