<template>
  <router-view />
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}

.hero-header {
  height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  background: #c04848; /* fallback for old browsers */
  background: linear-gradient(rgba(65, 97, 185, 0.8), rgba(133, 179, 201, 0.8)),
    url("https://ik.imagekit.io/ikmedia/blog/hero-image.jpeg"); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(rgba(0, 67, 72, 0.8), rgba(11, 73, 128, 0.8)),
    url("https://ik.imagekit.io/ikmedia/blog/hero-image.jpeg"); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  background-size: cover;
  background-repeat: no-repeat;
}
.signup-card,
.signin-card {
  position: relative;
  background-color: #fff;
  width: 450px;
  height: 500px;
  border-radius: 8px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.3);
}

.logo {
  width: 150px;
}

.signup-heading,
.signin-heading {
  font-size: 25px;
  text-transform: uppercase;
  font-weight: 900;
  margin-top: -15px;
  margin-bottom: 20px;
}

.signup-card input,
.signin-card input {
  display: block;
  padding: 10px;
  width: 90%;
  margin: auto;
  margin-bottom: 20px;
  border: 1px solid skyblue;
  outline: none;
  border-radius: 4px;
}

#submitBtn {
  width: 90%;
  height: 35px;
  margin-top: 20px;
  border: none;
  background: linear-gradient(to right, #7f7fd5, #86a8e7, #91eae4);
  cursor: pointer;
  border-radius: 2px;
  font-size: 16px;
  text-transform: uppercase;
  color: #fff;
}
p.register-here,
p.login-here {
  position: absolute;
  bottom: 20px;
  text-align: center;
  margin-left: 40%;
  transform: translate(-40%);
}

p.register-here a,
p.login-here a {
  text-transform: capitalize;
  font-weight: 500;
  color: #000;
}
</style>
