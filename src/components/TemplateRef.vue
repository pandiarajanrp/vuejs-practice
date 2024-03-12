<template>
  <div>
    <input type="text" ref="inputRef" />
    <Greet ref="greetRef" />
  </div>
</template>

<script>
import Greet from './Greet.vue';
export default {
  name: "TemplateRef",
  mounted() {
    console.log('Post Ref::', this.$refs.greetRef);
    this.$refs.inputRef.focus();
  },
  components: {
    Greet
  }
};
</script>

<style scoped>
</style>