<template>
  <div class="post">
    <router-link :to="{name: 'details', params: {id: post.id}}">
      <h3>{{ post.title }}</h3>
    </router-link>
    <p>{{ snipet }}</p>
    <span v-for="tag in post.tags" :key="tag">
      #{{ tag }}
    </span>
  </div>
</template>

<script>
import { computed } from '@vue/runtime-core'
export default {
props: ['post'],
setup(props) {
    const snipet = computed(() => {
       return props.post.body.substring(0, 100) + '...'
    })

    return {snipet}
}
}
</script>

<style>
  .post {
    border-bottom: 1px dashed #e7e7e7;
    padding-bottom: 30px;
    margin: 0 40px 30px !important;
  }
  .post a {
    text-decoration: none;
  }
  .post h3 {
    position: relative;
    color: #fff;
    display: inline-block;
    font-size: 26px;
    max-width: 400px;
    margin-bottom: 10px;
  }
  .post h3::before {
    position: absolute;
    content: "";
    background: #f80;
    width: 100%;
    height: 100%;
    z-index: -1;
    padding-right: 40px;
    left: -30px;
    transform: rotateZ(-1deg);
  }
</style>