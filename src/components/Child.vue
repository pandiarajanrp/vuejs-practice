<template>
  <div>
    This is Child Component
    <GrandChild />
  </div>
</template>

<script>
import GrandChild from "./GrandChild.vue";
export default {
  name: "ChildItem",
  components: {
    GrandChild,
  },
};
</script>

<style scoped>
</style>