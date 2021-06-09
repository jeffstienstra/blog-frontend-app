<template>
  <div>
    <h1>All Blog Posts</h1>
    <div>
      Search for something:
      <input type="text" v-model="searchFilter" list="post-titles" />
      <datalist id="post-titles">
        <option v-for="post in posts" v-bind:key="post.id">{{ post.title }}</option>
      </datalist>
    </div>

    <div
      class="row"
      is="transition-group"
      appear
      enter-active-class="animated fadeIn"
      leave-active-class="animated fadeOut"
    >
      <div v-for="post in filterBy(posts, searchFilter, 'title')" v-bind:key="post.id">
        <br />
        <img v-bind:src="post.image" alt="" style="width: 20%" />
        <h3>{{ post.title }}</h3>
        <h5>{{ post.body }}</h5>
        <a v-bind:href="`/posts/${post.id}`">More info</a>
        <br />
        <br />
      </div>
    </div>
  </div>
</template>

<style>
.card img {
  object-fit: cover;
  height: 300px;
}
.fadeOutLong {
  opacity: 0;
  transition: opacity 0.25s ease;
}
</style>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";

export default {
  mixins: [Vue2Filters.mixin],
  data: function () {
    return {
      posts: {},
      searchFilter: "",
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
