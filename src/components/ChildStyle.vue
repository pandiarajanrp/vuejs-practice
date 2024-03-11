<template>
  <div>
    <h4>This is from Child Style</h4>
  </div>
  <div class="content-heading">
    <slot name="heading"></slot>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
h4 {
  color: red;
}
.content-heading h4 {
  color: darkblue;
}
</style>