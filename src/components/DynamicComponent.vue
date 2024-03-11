<template>
  <div>
    Render Dynamic Components Based on Button. <br />
    <button @click="activeTab = 'tabA'">Tab A</button>
    <button @click="activeTab = 'tabB'">Tab B</button>
    <button @click="activeTab = 'tabC'">Tab C</button>
    <keep-alive>
      <component :is="activeTab" />
    </keep-alive>
  </div>
</template>

<script>
import TabA from "./TabA.vue";
import TabB from "./TabB.vue";
import TabC from "./TabC.vue";

export default {
  name: "DynamicComponent",
  data() {
    return {
      activeTab: "tabA",
    };
  },
  components: {
    TabA,
    TabB,
    TabC,
  },
};
</script>

<style scoped>
</style>