<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" msg2="world" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/template">template문법</RouterLink>
        <RouterLink to="/reactivity">Reactivity</RouterLink>
        <RouterLink to="/computed">Computed Properties</RouterLink>
        <RouterLink to="/binding">Class style Binding</RouterLink>
        <RouterLink to="/conditional">Conditional Rendering</RouterLink>
        <RouterLink to="/list">list Rendering</RouterLink>
        <RouterLink to="/event">event handling</RouterLink>
        <RouterLink to="/form">Form input binding</RouterLink>
        <RouterLink to="/lifecycle">Life Cycle</RouterLink>
        <RouterLink to="/watchers">Watchers</RouterLink>
        <RouterLink to="/refs">refs</RouterLink>
        <RouterLink to="/component">component basic </RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.layout {
  padding: 20px;
  border-top: 2px solid #ccc;
  margin-top: 40px;
}
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
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

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
