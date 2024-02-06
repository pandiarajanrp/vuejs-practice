<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h2>{{ name }}</h2>
  <div class="underline" v-bind:class="status">This is text</div>
  <div v-bind:id="containerId">This is content container</div>
  <p v-bind:class="isPromoted && 'promoted'">This is promoted content</p>
  <p v-bind:class="isSoldOut ? 'soldout' : 'new'">Soldout Movie</p>
  <p v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'soldout' : 'new']">
    Array Conditional Text
  </p>
  <p
    v-bind:class="{
      promoted: isPromoted,
      soldout: isSoldOut,
      new: isNew,
    }"
  >
    Object conditional class binding
  </p>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "Welcome to Vue JS",
      status: "danger",
      containerId: "content-wrapper",
      isPromoted: true,
      isSoldOut: false,
      isNew: true,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.promoted {
  font-style: italic;
}
.soldout {
  color: red;
}
.new {
  color: green;
  font-weight: bold;
}
</style>
