<template>
  <div id="nav">
    <Navigation />
  </div>
  <div class="container mt-4">
    <router-view />
  </div>
</template>
<script>
import Navigation from "@/components/Navigation.vue";
export default {
  components: { Navigation },
};
</script>
<style>
</style>
