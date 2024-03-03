<template>
    <div>
        This is Grand Child Component
        Name is - {{ name }}
    </div>
</template>

<script>
    export default {
        name: 'GrandChild',
        inject: ['name']
    }
</script>

<style scoped>

</style>