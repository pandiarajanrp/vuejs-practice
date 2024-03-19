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
    <input type="text" v-model="firstName" placeholder="Firstname" />
    <input type="text" v-model="lastName" placeholder="Lastname" />
    <input type="text" v-model="address.city" placeholder="City" />
    <button @click="changeUserName">Change Username</button>

    <h1>Computed</h1>
    <p>
      The fullname will generated based on the firstname and lastname in input
    </p>
    <h4>Computed Fullname - {{ computedFullname }}</h4>

    <h1>Provide Inject</h1>
    <ChildComp />

    <h1>Template Refs</h1>
    <input type="text" ref="inputRef" />

    <h1>Props and Events</h1>
    <ParentComp />
  </div>
</template>

<script>
import {
  ref,
  reactive,
  computed,
  watch,
  toRefs,
  provide,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";
import ChildComp from "./components/composition/Child.vue";
import ParentComp from "./components/composition/Parent.vue";

export default {
  name: "CompositionAPI",
  setup() {
    const name = ref("Pandiarajan");

    const inputRef = ref(null);

    const state = reactive({
      city: "Chennai",
      country: "India",
    });

    const userInfo = reactive({
      firstName: "",
      lastName: "",
      address: {
        city: "",
        state: "",
      },
    });

    const computedFullname = computed(function () {
      return `${userInfo.firstName} ${userInfo.lastName}`;
    });

    //watch for reactive vars
    watch(
      () => {
        return { ...userInfo };
      },
      (newValues, oldValues) => {
        console.log("newValues", newValues.firstName);
        console.log("oldValues", oldValues.firstName);
      }
      //{ immediate: true }
    );

    //watch individual property in reactive
    watch(
      () => userInfo.firstName,
      (newValue, oldValue) => {
        console.log("newValue :::", newValue);
        console.log("oldValue :::", oldValue);
      }
      //{ immediate: true }
    );

    //watch individual nestedproperty
    watch(
      () => Object.assign({}, userInfo.address),
      (newValue, oldValue) => {
        console.log("newValue :::", newValue);
        console.log("oldValue :::", oldValue);
      },
      { deep: true }
    );

    //watch for ref
    watch(
      [name],
      (newValues, oldValues) => {
        console.log({ newValues });
        console.log({ oldValues });
      },
      { immediate: true }
    );

    provide("refInfo", name);
    provide("reactiveInfo", userInfo);

    function changeName() {
      name.value = "Rajagopal";
    }

    function changeState() {
      (state.city = "Mexico City"), (state.country = "Mexico");
    }

    function changeUserName() {
      (userInfo.firstName = "Pandiarajan"), (userInfo.lastName = "Rajagopal");
    }

    // life cycle
    onBeforeMount(() => {
      console.log("Mount - Life Cycle Hooks");
    });
    onMounted(() => {
      console.log("**** inputRef", inputRef);
      inputRef.value.focus();
      console.log("Mounted - Life Cycle Hooks");
    });
    onBeforeUpdate(() => {
      console.log("Update - Life Cycle Hooks");
    });
    onUpdated(() => {
      console.log("Updated - Life Cycle Hooks");
    });
    onBeforeUnmount(() => {
      console.log("UnMount - Life Cycle Hooks");
    });
    onUnmounted(() => {
      console.log("UnMounted - Life Cycle Hooks");
    });

    return {
      name,
      changeName,
      changeState,
      changeUserName,
      computedFullname,
      inputRef,
      ...toRefs(state),
      ...toRefs(userInfo),
    };
  },
  components: {
    ChildComp,
    ParentComp,
  },
};
</script>

<style scoped>
</style>