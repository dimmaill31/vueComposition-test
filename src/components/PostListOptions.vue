<template>
    <div v-if="posts.length >= 1">
        <PostItem v-for="post in posts" :post="post" :key="post.id" @deletePost="deletePost"/>
    </div>
    <div v-else>
        <h2>posts is not defined</h2>
    </div>
</template>

<script>
import PostItem from './PostItem.vue';
export default {
    setup () {
        

        return {}
    },
    components: {
        PostItem,
      },
    props: {
        posts: {
          type: Array,
          required: true,
        }
    },
    methods: {
        deletePost(postId) {
            this.$emit('deletePost', postId)
        }
    }
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