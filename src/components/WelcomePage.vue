<template>
  <header>
    <div class="container">
      <input type="checkbox" name="check" id="check" />

      <div class="logo-container">
        <h3 class="logo">Brand<span>Name</span></h3>
      </div>

      <div class="nav-btn">
        <div class="log-sign" style="--i: 1.8s">
          <router-link to="/sign-in"
            ><a href="#" class="btn transparent">Log in</a></router-link
          >
          <router-link to="/sign-up"
            ><a href="#" class="btn solid">Sign up</a></router-link
          >
        </div>
      </div>

      <div class="hamburger-menu-container">
        <div class="hamburger-menu">
          <div></div>
        </div>
      </div>
    </div>
  </header>

  <main>
    <section>
      <div class="overlay"></div>
    </section>
    <h1 class="app-name">restaurant management system</h1>
  </main>
</template>

<script>
export default {
  name: "WelcomePage",
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>

<style>
h1.app-name {
  position: absolute;
  color: #fff;
  z-index: 1000;
  text-transform: uppercase;
  font-size: 2rem;
  text-align: center;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
:root {
  --clr-bg-header: #3d8361;
  --clr-btn: #3d8361;
  --clr-nav-hover: #1e6f5c;
  --clr-light: #fafafa;
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
}

header {
  position: sticky;
  top: 0px;
  background-color: var(--clr-bg-header);
  width: 100%;
  z-index: 1000;
}

section {
  position: relative;
  height: calc(100vh - 3rem);
  width: 100%;
  background: url("https://ik.imagekit.io/ikmedia/blog/hero-image.jpeg")
    no-repeat top center / cover;
  overflow: hidden;
}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-color: rgba(30, 130, 95, 0.5);
}

.container {
  max-width: 65rem;
  padding: 0 2rem;
  margin: 0 auto;
  display: flex;
  position: relative;
}

.logo-container {
  flex: 1;
  display: flex;
  align-items: center;
}

.nav-btn {
  flex: 3;
  display: flex;
}

.nav-links {
  flex: 2;
}

.nav-links > ul {
  display: flex;
  justify-content: center;
  align-items: center;
}

.nav-link {
  position: relative;
}

.nav-link > a {
  line-height: 3rem;
  color: var(--clr-light);
  padding: 0 0.8rem;
  letter-spacing: 1px;
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  transition: 0.5s;
}

.nav-link > a > i {
  margin-left: 0.2rem;
}

.nav-link:hover > a {
  transform: scale(1.1);
}

.log-sign {
  display: flex;
  justify-content: right;
  align-items: center;
  flex: 1;
}

.logo {
  color: var(--clr-light);
  font-size: 1.1rem;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  line-height: 3rem;
  cursor: pointer;
}

.logo span {
  font-weight: 300;
}

.btn {
  display: inline-block;
  padding: 0.5rem 1.3rem;
  font-size: 0.8rem;
  border: 2px solid var(--clr-light);
  border-radius: 2rem;
  line-height: 1;
  margin: 0 0.2rem;
  transition: 0.3s;
  text-transform: uppercase;
}

.btn.solid,
.btn.transparent:hover {
  background-color: var(--clr-light);
  color: var(--clr-btn);
}

.btn.transparent,
.btn.solid:hover {
  background-color: transparent;
  color: var(--clr-light);
}

.hamburger-menu-container {
  flex: 1;
  display: none;
  align-items: center;
  justify-content: flex-end;
}

.hamburger-menu {
  width: 2.5rem;
  height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.hamburger-menu div {
  width: 1.6rem;
  height: 3px;
  border-radius: 3px;
  background-color: var(--clr-light);
  position: relative;
  z-index: 1001;
  transition: 0.5s;
}

.hamburger-menu div:before,
.hamburger-menu div:after {
  content: "";
  position: absolute;
  width: inherit;
  height: inherit;
  background-color: var(--clr-light);
  border-radius: 3px;
  transition: 0.5s;
}

.hamburger-menu div:before {
  transform: translateY(-7px);
}

.hamburger-menu div:after {
  transform: translateY(7px);
}

#check {
  position: absolute;
  top: 50%;
  right: 1.5rem;
  transform: translateY(-50%);
  width: 2.5rem;
  height: 2.5rem;
  z-index: 90000;
  cursor: pointer;
  opacity: 0;
  display: none;
}

#check:checked ~ .hamburger-menu-container .hamburger-menu div {
  background-color: transparent;
}

#check:checked ~ .hamburger-menu-container .hamburger-menu div:before {
  transform: translateY(0) rotate(-45deg);
}

#check:checked ~ .hamburger-menu-container .hamburger-menu div:after {
  transform: translateY(0) rotate(45deg);
}

@keyframes animation {
  from {
    opacity: 0;
    transform: translateY(15px);
  }

  to {
    opacity: 1;
    transform: translateY(0px);
  }
}

@media (max-width: 920px) {
  .hamburger-menu-container {
    display: flex;
  }

  #check {
    display: block;
  }

  .nav-btn {
    position: fixed;
    height: calc(100vh - 3rem);
    top: 3rem;
    left: 0;
    width: 100%;
    background-color: var(--clr-btn);
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    overflow-x: hidden;
    overflow-y: auto;
    transform: translateX(100%);
    transition: 0.65s;
  }

  #check:checked ~ .nav-btn {
    transform: translateX(0);
  }

  #check:checked ~ .nav-btn .nav-link,
  #check:checked ~ .nav-btn .log-sign {
    animation: animation 0.5s ease forwards var(--i);
  }

  .nav-links {
    flex: initial;
    width: 100%;
  }

  .nav-links > ul {
    flex-direction: column;
  }

  .nav-link {
    width: 100%;
    opacity: 0;
    transform: translateY(15px);
  }

  .nav-link > a {
    line-height: 1;
    padding: 1.6rem 2rem;
  }

  .nav-link:hover > a {
    transform: scale(1);
    background-color: var(--clr-nav-hover);
  }

  .log-sign {
    flex: initial;
    width: 100%;
    padding: 1.5rem 1.9rem;
    justify-content: flex-start;
    opacity: 0;
    transform: translateY(15px);
  }
}
</style>
