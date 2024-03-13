<template>
  <div>
    <h2>Composition API</h2>
    <h4>{{ name }}</h4>
    <button @click="changeName">Change Name</button>
    <h2>State - {{ city }}, {{ country }}</h2>
    <button @click="changeState">Change State</button>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";

export default {
  name: 'CompositionAPI',
  setup() {
    const name = ref('Pandiarajan');
    const state = reactive({
      city: 'Chennai',
      country: 'India'
    });
    function changeName() {
      name.value = "Rajagopal";
    }

    function changeState() {
      state.city = 'Mexico City',
      state.country = 'Mexico'
    }
    return {
      name,
      changeName,
      changeState,
      ...toRefs(state),
    }
  },
};
</script>

<style scoped>
</style>