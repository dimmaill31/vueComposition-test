<template>
    <div class="post">
        <h2>
            {{ post.title }}
        </h2>
        <p>
            {{ post.text }}
        </p>
        <button class="post__btn" @click="deletePost">
            delete
        </button>
    </div>
</template>

<script setup>

import { defineProps, defineEmits } from 'vue'

const props = defineProps({
    post:{
        type: Object,
        required: true,
    }
})

const emits = defineEmits(['deletePost'])

const deletePost = function() {
    emits('deletePost', props.post.id)
}

</script>

<style scoped>

.post{
  display: flex;
  margin: 0 auto;
  max-width: 500px;
  width: 100%;
  border: 1px solid black;
  border-radius: 15px;
  padding: 30px;
  justify-content: space-between;
  align-items: center;
}

.post__btn{
  padding: 15px;
  border: none;
  border-radius: 15px;
  background-color: black;
  color: white;
}

</style>