<template>
    <div class="app">
        <MyButton @click="openPopup">
            open form
        </MyButton>
        <MyModal v-show="modalShowStatus" v-model:modalShowStatus="modalShowStatus">
            <PostForm @createPost="createPost"/>
        </MyModal>
        <PostList v-bind:posts="posts" @deletePost="deletePost"/>
    </div>
</template>

<script setup>
    import PostList from './components/PostList.vue';
    import { ref } from 'vue';

    const posts = ref([ 
                    {id: 1, title: 'Gigabytes', text: 'a lot of gigabytes',},
                    {id: 2, title: 'Megabytes', text: 'a lot of megabytes',},
                    {id: 3, title: 'Kilobytes', text: 'a lot of kilobytes',}
                ])

    const createPost = function(newPost) {
        posts.value.push(newPost)
    }

    const deletePost = function(postID) {
        posts = posts.value.filter(post => post.id !== postID)
    }

    const openPopup = function() {
        modalShowStatus.value = true;
    }

    const closePopup = function() {
        modalShowStatus.value = false;
    }
</script>

<style>

</style>