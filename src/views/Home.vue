<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>Signup and find your soap box.</h3>
    <a href="/posts">see all blog posts</a>
  </div>
</template>

<style></style>

<script>
export default {
  data: function () {
    return {
      message: "Start a blog, say some stuff.",
    };
  },
  created: function () {},
  methods: {},
};
</script>
