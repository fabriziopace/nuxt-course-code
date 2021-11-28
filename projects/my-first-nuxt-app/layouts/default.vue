<template>
  <div>
    <Header />
    <nuxt />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
export default {
  components: {
    Header,
  },
};
</script>

<style>
html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
}
</style>
