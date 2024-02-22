<template>
  <div>
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
    <p :class="isShort ? 'short' : 'non-short'">V bind Shorthand</p>
    <h1>Conditional Rendering</h1>
    <h4 v-if="num===0">Num is Zero</h4>
    <h4 v-else-if="num > 0">Positive</h4>
    <h4 v-else-if="num < 0">Negative</h4>
    <h4 v-else>Not a Number</h4>
    <h1>Conditional Rendering With Multiple Element</h1>
    <template v-if="showConditions">
      <p>Terms and conditions</p>
      <p>Privacy Policy</p>
      <p>Agree to Policy</p>
    </template>
  </div>
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
      isShort: true,
      num: 5,
      showConditions: true
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
.short {
  color: magenta;
}
h1 {
  border: 1px solid #eee;
}
</style>
