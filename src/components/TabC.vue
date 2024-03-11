<template>
    <div>
        Tab C Content with Keep Alive
        <input type="text" v-model="description" />
    </div>
</template>

<script>
    export default {
        name: 'TabC',
        data() {
            return {
                description: ''
            }
        }
    }
</script>

<style scoped>

</style>