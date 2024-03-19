<template>
  <div>
    <h2>This is Parent Component</h2>
    <ParentGreeting
      :firstName="firstName"
      :lastName="lastName"
      @callHandler="callHandler"
    />
  </div>
</template>

<script>
import ParentGreeting from "./ParentGreeting.vue";
import { ref } from "vue";
export default {
  name: "ParentComp",
  setup() {
    const firstName = ref("Pandiarajan");
    const lastName = ref("Rajagopal");

    function callHandler(fullName) {
      alert(fullName);
    }

    return {
      firstName,
      lastName,
      callHandler,
    };
  },
  components: {
    ParentGreeting,
  },
};
</script>

<style scoped>
</style>