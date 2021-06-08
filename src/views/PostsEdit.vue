<template>
  <div>
    <form v-on:submit.prevent="updatePost()">
      <h1>Edit Post</h1>
      <div>
        <label>Title:</label>
        <input type="text" v-model="editPostParams.title" />
      </div>
      <div>
        <label>Body:</label>
        <input type="text" v-model="editPostParams.body" />
      </div>
      <div>
        <label>image:</label>
        <input type="text" v-model="editPostParams.image" />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      editPostParams: {},
    };
  },
  created: function () {
    this.showPost();
  },
  methods: {
    showPost: function () {
      axios.get("/posts/" + this.$route.params.id).then((response) => {
        console.log("show posts", response.data);
        this.editPostParams = response.data;
      });
    },
    updatePost: function () {
      axios.patch("posts/" + this.$route.params.id, this.editPostParams).then((response) => {
        console.log(response.data);
        this.$router.push("/posts");
      });
    },
  },
};
</script>
