<template>
  <div>
    <h2>This is Child Component</h2>
    <h4>Fullname is {{ fullName }}</h4>
    <button @click="sendEvent">Call Handler</button>
  </div>
</template>
  
  <script>
import { computed } from "vue";
export default {
  name: "ParentGreeting",
  setup(props, context) {
    console.log({ context });
    const fullName = computed(() => {
      return `${props.firstName} ${props.lastName}`;
    });
    function sendEvent() {
      context.emit("callHandler", fullName.value);
    }
    return {
      fullName,
      sendEvent,
    };
  },
  props: ["firstName", "lastName"],
  emits: ["callHandler"],
};
</script>
  
  <style scoped>
</style>