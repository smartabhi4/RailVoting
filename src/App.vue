<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div style="display: flex; flex-direction: column">
    <div class="img_class">
      <img
        alt="Vue logo"
        class="logo"
        src="https://media-hosting.imagekit.io//0b981e1d01c1454b/RAIL%20LOGO.jpg?Expires=1733412683&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=VM5kfMAG0uknK64Tg-C8r7azK3DVy4LxY5Ta4Xiu-x3hH67fNh1S~Zo2xqhUg8RBAFkyEKd6olmBNq7KDlM--4wzJDe5luRKFHamMfxYjAZ8xt3FVlDiXR050~-miGGD3jzijPGA6CC-4S6Ae8QNRh2UAuslBVFQjE6g4De-be9dOQyxuRheTcwG2yI64fm-JY0BfcYFeA0xS4SRlhHZeksmlO7PQiBUCqtPLy3~s4bg~9gSjP7h5w--X-Y~GTmbcG3FeqV2fmecwyIBeytH9NssT0OVHclJV2uvBG~VxmVfH7lcpOninC0fcC8bz15ao0XdZST-s~cpDLgp9yWusg__"
        width="125"
        height="125"
      />
    </div>
    <HelloWorld></HelloWorld>
    <RouterView />
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.img_class {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 30px;
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
    margin-top: 100px;
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
