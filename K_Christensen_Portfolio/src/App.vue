<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Tagline from './components/TagLine.vue'
</script>

<template>

  <div class="profile">
  <header>
    <img alt="Photo of Kinsey" class="logo" src="@/assets/KChristensen.jpg"/>

    <div class="wrapper">
      <Tagline msg="Kinsey Christensen" id="tagline"/>

      <nav id="nav-links">
        <RouterLink to="/">About Me</RouterLink>
        <RouterLink to="/projects">Projects</RouterLink>
        <a href=" https://www.linkedin.com/in/kinsey-christensen/">My LinkedIn</a> 
      </nav>
    </div>
  </header>

  <RouterView class="router"/>
  

  <footer><a href="https://www.flaticon.com/free-icons/flower" title="flower icons">Flower icons created by Freepik - Flaticon</a>
          | <a href='https://medium.com/@prachishah03737/vue-3-image-slider-from-scratch-for-beginners-a-step-by-step-tutorial-with-composition-api-03a0aa21fc60'>Image Slider by Prachi Shah</a> </footer>
</div>
</template>

<style scoped>
header {
  max-height: 100vh;
  display: grid;
 grid-template-columns: 1fr;
 grid-template-areas: 
 "logo"
 "wrapper";
 margin-top: 40px;
}

.wrapper {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-areas: "nav" "tagline";
}

.logo {
 margin: auto;
  max-width: 206px;
  max-height: 256px;
  border-radius: 20px;
  grid-area: logo;
  border-color: rgb(246, 66, 180);
  border-style: double;
  
}
.wrapper{
  grid-area: wrapper;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;

  
}
#nav-links{
  grid-area: nav;
  
}
#tagline{
  grid-area: tagline;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

footer{
  margin-top: 10px;
  font-size: small;
}


@media (min-width: 1024px) {
  header {
    display: flex;
    max-width: 50vw;
   grid-area: header;
  }

  .logo {
    margin: 0px;
  

  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
    padding: 15px;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
 
  }
  .profile{
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-areas:
    "header router"
    ". router"
    ". footer"
    ;
 
  }
  footer {
    grid-area: footer;
  }
  .router{
    grid-area: router;
  }
}
</style>
