<template>
    <form class="form" @submit.prevent>
      <MyInput class="form__input" type="text" placeholder="enter title" v-model="title"/>
      <MyInput class="form__input" type="text" placeholder="enter text" v-model="text"/>
      <MyButton class="form__btn" @click="createPost">
        create
      </MyButton>
    </form>
</template>

<script setup>
import { ref } from 'vue';

const title = ref('')
const text = ref('')

const createPost = function() {
  const newPost = {
    id: Date.now(),
    title: this.title,
    text: this.text,
  }
  this.$emit('createPost', newPost)
  this.title = ''
  this.text = ''
}

</script>

<style scoped>

.form{
  flex-direction: column;
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

.form__input{
  display: block;
  max-width: 150px;
  width: 100%;
  border: 1px solid black;
  border-radius: 15px;
  padding: 15px;
}

.form__btn{
  padding: 15px;
  border: none;
  border-radius: 15px;
  background-color: black;
  color: white;
}

</style>