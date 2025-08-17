<template>
    <div class="app">
        <MyButton @click="openPopup">
            open popup
        </MyButton>
        <TestModal v-show="modalShowStatus" v-model:modalShowStatus="modalShowStatus">
            <PostForm @createPost="createPost"/>
        </TestModal>
        <PostList v-bind:posts="posts" @deletePost="deletePost"/>
    </div>
</template>

<script>
import PostList from './components/PostList.vue'
import PostForm from './components/PostForm.vue'

export default {
    components: {
      PostList, 
      PostForm,
    },
    setup () {
        

        return {
            posts: [ 
                {id: 1, title: 'Gigabytes', text: 'a lot of gigabytes',},
                {id: 2, title: 'Megabytes', text: 'a lot of megabytes',},
                {id: 3, title: 'Kilobytes', text: 'a lot of kilobytes',}
            ],
            modalShowStatus: false,
        }
    },
    methods: {
      createPost(newPost) {
        this.posts.push(newPost)
      },
      deletePost(postId) {
        this.posts = this.posts.filter(post => post.id !== postId)
      },
      openPopup() {
        this.modalShowStatus = true;
      },
      closePopup() {
        this.modalShowStatus = false;
      },
    }
}
</script>

<style scoped>

.form{
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