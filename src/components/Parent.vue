<template>
  <div>
    This is Parent Component Name is - {{ username }}
    <Child />
  </div>
</template>

<script>
import Child from "./Child.vue";
export default {
  name: "ParentItem",
  components: {
    Child,
  },
  data() {
    return {
      username: "Pandiarajan Rajagopal",
    };
  },
  provide() {
    return {
        name: this.username
    }
    
  },
};
</script>

<style scoped>
</style>