<template>
  <div>
    This is Parent Component Name is - {{ username }}
    <button type="button" @click="showChild = !showChild">Show Child</button>
    <Child v-if="showChild"/>
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
      showChild: false,
    };
  },
  provide() {
    return {
        name: this.username
    }
  },
  beforeCreate() {
    console.log('Parent beforeCreate()')
  },
  created() {
    console.log('Parent created()')
  },
  beforeMount() {
    console.log('Parent beforeMount()')
  },
  mounted() {
    console.log('Parent mounted()')
  },
  beforeUpdate() {
    console.log('Parent beforeUpdate()')
  },
  updated() {
    console.log('Parent updated()')
  },
  beforeUnmount() {
    console.log('Parent beforeUnmount()')
  },
  unmounted() {
    console.log('Parent unmounted()')
  }
};
</script>

<style scoped>
</style>