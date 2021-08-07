<template>
  <div id="app">
    <div class="container">
      <navApp />
      <router-view />
    </div>
  </div>
</template>

<script>
import navApp from "@/components/Navbar";
export default {
  components: {
    navApp,
  },
};
</script>

<style>
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
