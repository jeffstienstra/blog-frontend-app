<template>
  <div>
    <h1>All Blog Posts</h1>
    <p>{{ posts }}</p>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      posts: {},
    };
  },
  created: function () {
    this.postsIndex();
  },
  methods: {
    postsIndex: function () {
      console.log("blog posts");
    },
  },
};
</script>
