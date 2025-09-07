<template>
    <div class="app">
        <MyButton @click="openPopup" class="openPopup__btn">
            open form
        </MyButton>
        <MyModal v-show="modalShowStatus" v-model:modalShowStatus="modalShowStatus" @closePopup="closePopup">
            <PostForm @createPost="createPost"/> 
        </MyModal>
        <PostList v-bind:posts="posts" @deletePost="deletePost"/>
    </div>
</template>

<script setup>
    import MyButton from './components/UI/MyButton.vue';
    import PostForm from './components/PostForm.vue';
    import MyModal from './components/UI/MyModal.vue';

    import PostList from './components/PostList.vue';
    import { ref } from 'vue';

    let posts = ref([ 
                    {id: 1, title: 'Gigabytes', text: 'a lot of gigabytes',},
                    {id: 2, title: 'Megabytes', text: 'a lot of megabytes',},
                    {id: 3, title: 'Kilobytes', text: 'a lot of kilobytes',}
                ])
    
    let modalShowStatus = ref(false)

    const createPost = function(newPost) {
        posts.value.push(newPost)
    }

    const deletePost = function(postID) {
        posts.value = posts.value.filter(post => post.id !== postID)
        console.log(posts)
    }

    const openPopup = function() {
        modalShowStatus.value = true;
        console.log(modalShowStatus.value)
    }

    const closePopup = function() {
        modalShowStatus.value = false;
    }
</script>

<style>

.app{
    display: flex;
    flex-direction: column;
    align-items: center;
}

.openPopup__btn{
    padding: 15px;
    border: none;
    border-radius: 15px;
    background-color: black;
    color: white;
}

</style>