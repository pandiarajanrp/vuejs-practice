<template>
  <div>
    <h2>Clicked Count {{ count }}</h2>
    <input type="button" @click="incrementCount" value="Click"/>
  </div>
</template>

<script>
import counterMixin from '../mixins/counter';

export default {
  name: "MixinsItem",
  mixins: [counterMixin]
};
</script>

<style scoped>
</style>