<template>
    <div>
        <input type="text" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
    </div>
</template>

<script>
    export default {
        name: 'InputItem',
        props: {
            modelValue: String
        }
    }
</script>