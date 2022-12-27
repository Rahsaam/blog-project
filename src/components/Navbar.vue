<template>
  <div class="navbar">
    <h1>Dojo blog</h1>
    <nav>
        <router-link :to="{name: 'home'}">Home</router-link>
        <router-link :to="{name: 'Create'}">Create post</router-link>
    </nav>
  </div>
</template>

<script>
export default {

}
</script>

<style>
    .navbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        max-width: 1400px;
        margin: 0 auto;
        padding: 10px;
    }
    .navbar h1 {
        color: #dfdfdf;
        font-size: 48px;
    }
    .navbar a {
        color: #bbb;
        text-decoration: none;
        margin-left: 20px;
    }
    .navbar a.router-link-active {
        color: #444;
        font-weight: bold;
    }
</style>