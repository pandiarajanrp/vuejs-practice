<template>
  <div>
    <form @submit.prevent="createPost">
      <label>Title</label>
      <input type="text" v-model="formData.title" />
      <label>Description</label>
      <input type="text" v-model="formData.body" />
      <label>User ID</label>
      <input type="text" v-model="formData.userId" />
      <button type="submit">Create Post</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "CreatePost",
  data() {
    return {
      formData: {
        title: "",
        body: "",
        userId: "",
      },
    };
  },
  methods: {
    createPost() {
      console.log(this.formData);
      fetch("https://jsonplaceholder.typicode.com/posts", {
        method: "POST",
        body: JSON.stringify(this.formData),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => console.log("Response", json))
        .catch((err) => console.log("Err", err));
    },
  },
};
</script>

<style scoped>
</style>