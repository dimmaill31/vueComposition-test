<template>
    <input :value="modelValue" @input="updateInput">
</template>

<script setup>
    const props = defineProps({
        modelValue: {
            type: [Number, String],
            required: true,
        }
    })

    const emits = defineEmits(['updateInput'])

    const updateInput = function(event) {
        emits('update:modelValue', event.target.value)
    }
</script>

<style scoped>

</style>