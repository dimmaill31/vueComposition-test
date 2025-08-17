<template>
    <input :value="modelValue" @input="updateInput">
</template>

<script>
    export default {
        name: 'MyInput',
        props: {
            modelValue: {
                type: [Number, String],
                required: true,
            }
        },
        methods: {
            updateInput(event) {
                this.$emit('update:modelValue', event.target.value)
            }
        } 
    }
</script>

<style scoped>

</style>