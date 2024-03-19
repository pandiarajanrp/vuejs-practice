<template>
  <div>
    <h4>Child Ref Component - {{ name }}</h4>
    <h4>Child Reactive Component - {{ firstName }} {{ lastName }}</h4>
  </div>
</template>

<script>
import { inject, toRefs } from "vue";
export default {
  name: "ChildComp",
  setup() {
    const name = inject("refInfo");
    const reactiveInfo = inject("reactiveInfo");

    return {
      name,
      ...toRefs(reactiveInfo),
    };
  },
};
</script>

<style scoped>
</style>