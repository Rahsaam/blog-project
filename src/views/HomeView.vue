<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts"/>
    </div>
    <div v-else>
      <!-- <p>loading...</p> -->
      <Spinner />
    </div>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import Spinner from '../components/Spinner.vue'
import getPosts from '../composables/getPosts'



export default {
  name: '',
  components: { PostList, Spinner },
  setup() {
    
    const {posts, error, load} = getPosts()
    load()

    return {posts, error}
  }
}
</script>

<style>
  .home {
    max-width: 1400px;
    margin: 0 auto;
    padding: 10px;
  }
</style>
