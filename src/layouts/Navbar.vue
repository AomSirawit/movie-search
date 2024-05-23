<template>
  <div class="navbar bg-slate-800 p-2 justify-between sticky top-0 z-50">
    <h1 class="btn btn-ghost text-2xl text-white">MovieSearch</h1>
    <div>
      <a class="btn btn-ghost text-white" href="/" v-smooth-scroll>Home</a>
      <a class="btn btn-ghost text-white" href="#search" v-smooth-scroll>Search</a>
      <a class="btn btn-ghost text-white" href="#recommended" v-smooth-scroll>Recommended</a>
      <a class="btn btn-ghost text-white" href="#faq" v-smooth-scroll>Faq</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style>
/* Add your styles here if needed */
</style>
