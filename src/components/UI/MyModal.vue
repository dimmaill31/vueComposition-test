<template>
    <div class="modal" @click="closePopup">
        <div class="modal__content" @click.stop>
            <slot></slot>
        </div>
    </div>
</template>

<script setup>
    import { defineProps, defineEmits } from 'vue'

    const props = defineProps({
        modalShowStatus: {
            type: Boolean,
            required: true,
        }
    })

    const emits = defineEmits(['closePopup'])
    
    const closePopup = function() {
        emits('closePopup')
    }
</script>

<style scoped>

.modal{
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.6);
    justify-content: center;
    align-items: center;
    display: flex;
    visibility: visible;
    max-width: 900px;
    width: 100%;
}

</style>