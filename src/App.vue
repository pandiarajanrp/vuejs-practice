<template>
  <div class="container">
    <div class="flex-item">
      <OptionsAPI />
    </div>
    <div class="flex-item">
      <CompositionAPI />
    </div>
  </div>
</template>

<script>
import OptionsAPI from './OptionsAPI.vue';
import CompositionAPI from './CompositionAPI.vue';

export default {
  name: "App",
  components: {
    OptionsAPI,
    CompositionAPI
  }
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
h4 {
  color: goldenrod;
}
.container {
  display: flex;
}
.flex-item {
  border: 2px solid #ccc;
  padding: 15px;
  flex-grow: 2;
}
</style>
