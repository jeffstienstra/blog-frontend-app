<template>
  <div>
    <h1>One Post</h1>
    <img v-bind:src="post.image" alt="" style="width: 20%" />
    <h2>{{ post.title }}</h2>
    <h2>{{ post.body }}</h2>
    <a href="/posts">Back to all posts</a>
    <a v-bind:href="`/posts/${post.id}/edit`">Edit this post</a>
    <br />
    <br />
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      post: {},
    };
  },
  created: function () {
    this.PostsShow();
  },
  methods: {
    PostsShow: function () {
      axios.get("/posts/" + this.$route.params.id).then((response) => {
        console.log("show a post", response.data);
        this.post = response.data;
      });
    },
  },
};
</script>
