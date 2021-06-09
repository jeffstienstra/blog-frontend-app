<template>
  <div>
    <h1>One Post</h1>
    <img v-bind:src="post.image" alt="" style="width: 20%" />
    <h3>{{ post.title }}</h3>
    <h5>{{ post.body }}</h5>
    <a v-if="post.is_owner" v-bind:href="`/posts/${post.id}/edit`">Edit this post</a>
    <button v-if="post.is_owner" v-on:click="destroyPost()">Destroy post</button>
    <a href="/posts">Back to all posts</a>
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
    destroyPost: function () {
      console.log("destroy post", this.post);
      axios.delete("/posts/" + this.post.id).then((response) => {
        console.log("Destroy success", response.data);
        this.$router.push("/posts");
      });
    },
  },
};
</script>
