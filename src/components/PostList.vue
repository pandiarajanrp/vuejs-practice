<template>
  <div>
    <div v-for="post in posts" :key="post.id">
        <h2>{{ post.title }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "PostList",
  data() {
    return {
      posts: [],
    };
  },
  created() {
    this.getPosts()
  },
  methods: {
    getPosts() {
      fetch("https://jsonplaceholder.typicode.com/posts")
        .then((res) => res.json())
        .then((res) => {
          console.log("posts response", res);
          this.posts = res.slice(0,10);
        })
        .catch((err) => {
          console.log("Err:", err);
        });
    },
  },
};
</script>

<style scoped>
</style>