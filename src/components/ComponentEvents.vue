<template>
    <div>
        Show Information Modal
        <button @click="showModal = true">Open Modal</button>
        <PopupModal v-if="showModal" @close="closeModal"/>
    </div>
</template>

<script>
    import PopupModal from './PopupModal.vue';
    export default {
        name: 'ComponentEvents',
        data() {
            return {
                showModal: false
            }
        },
        methods: {
            closeModal(data) {
                console.log('data from event', data)
                this.showModal = false;
            }
        },
        components: {
            PopupModal
        }
    }
</script>

<style scoped>

</style>