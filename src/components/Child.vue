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
  beforeCreate() {
    console.log('Child beforeCreate()')
  },
  created() {
    console.log('Child created()')
  },
  beforeMount() {
    console.log('Child beforeMount()')
  },
  mounted() {
    console.log('Child mounted()')
  },
  beforeUpdate() {
    console.log('Child beforeUpdate()')
  },
  updated() {
    console.log('Child updated()')
  },
  beforeUnmount() {
    console.log('Child beforeUnmount()')
  },
  unmounted() {
    console.log('Child unmounted()')
  }
};
</script>

<style scoped>
</style>