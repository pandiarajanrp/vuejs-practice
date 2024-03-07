<template>
  <div>
    <template v-for="name in nameList" :key="name.firstName">
        <slot :firstName="name.firstName" :lastName="name.lastName"></slot>
    </template>
    
  </div>
</template>

<script>
export default {
  name: "NameList",
  data() {
    return {
      nameList: [
        {
          firstName: "Bruce",
          lastName: "Cyan",
        },
        {
          firstName: "Jon",
          lastName: "Smith",
        },
        {
          firstName: "Waren",
          lastName: "Bhat",
        },
      ],
    };
  },
};
</script>

<style scoped>
</style>