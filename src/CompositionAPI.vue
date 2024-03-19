<template>
  <div>
    <h2>Composition API</h2>
    <h1>Data</h1>
    <h4>{{ name }}</h4>
    <button @click="changeName">Change Name</button>
    <h1>Methods</h1>
    <h2>State - {{ city }}, {{ country }}</h2>
    <button @click="changeState">Change State</button>
    <h1>V-Model</h1>
    <input type="text" v-model="firstName" />
    <input type="text" v-model="lastName" />
    <button @click="changeUserName">Change Username</button>
    <h1>Computed</h1>
    <p>
      The fullname will generated based on the firstname and lastname in input
    </p>
    <h4>Computed Fullname - {{ computedFullname }}</h4>
  </div>
</template>

<script>
import { ref, reactive, computed, watch, toRefs } from "vue";

export default {
  name: "CompositionAPI",
  setup() {
    const name = ref("Pandiarajan");

    const state = reactive({
      city: "Chennai",
      country: "India",
    });

    const userInfo = reactive({
      firstName: "",
      lastName: "",
    });

    const computedFullname = computed(function () {
      return `${userInfo.firstName} ${userInfo.lastName}`;
    });

    watch(
      [name],
      (newValues, oldValues) => {
        console.log({ newValues });
        console.log({ oldValues });
      },
      { immediate: true }
    );

    function changeName() {
      name.value = "Rajagopal";
    }

    function changeState() {
      (state.city = "Mexico City"), (state.country = "Mexico");
    }

    function changeUserName() {
      (userInfo.firstName = "Pandiarajan"), (userInfo.lastName = "Rajagopal");
    }

    return {
      name,
      changeName,
      changeState,
      changeUserName,
      computedFullname,
      ...toRefs(state),
      ...toRefs(userInfo),
    };
  },
};
</script>

<style scoped>
</style>