<template>
  <div>
    <slot>Default Content</slot>

    <div class="header">
      <slot name="header"></slot>
    </div>
    <div class="card">
      <slot name="default"></slot>
    </div>
    <div class="footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardSlot",
};
</script>

<style scoped>
</style>