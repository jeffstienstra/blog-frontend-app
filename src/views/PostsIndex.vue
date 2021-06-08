<template>
  <div>
    <h1>All Blog Posts</h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <img v-bind:src="post.image" alt="" style="width: 20%" />
      <h2>{{ post.title }}</h2>
      <h2>{{ post.body }}</h2>
      <a v-bind:href="`/posts/${post.id}`">More info</a>
      <br />
      <br />
    </div>
  </div>
</template>

<script>
import axios from "axios";

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
      axios.get("/posts").then((response) => {
        console.log("blog posts", response);
        this.posts = response.data;
      });
    },
  },
};
</script>
