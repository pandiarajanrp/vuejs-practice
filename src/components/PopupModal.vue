<template>
  <div>
    Opened Modal Informations below
    <button @click="$emit('close', 'event data')">Close Modal</button>
  </div>
</template>

<script>
export default {
  name: "PopupModal",
  emits: {
    close(name) {
      if (name) return true;
      return false;
    },
  },
};
</script>

<style scoped>
</style>