<template>
  <div class="create">
    <form @submit.prevent="handleSubmit">
        <label>Title: </label>
        <input v-model="title" type="text" required>
        <label>Content:</label>
        <textarea v-model="body" required></textarea>
        <label>Tags (hit enter to add tags)</label>
        <input
         v-model="tag"
         type="text"
         @keydown.enter.prevent="addTag" 
         >
         <div v-for="tag in tags" :key="tag" class="pill">
            #{{ tag }}
        </div>
        <button>Add post</button>
    </form>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'
import { onMounted } from '@vue/runtime-core'
import { json } from 'body-parser'
import { useRouter } from 'vue-router'
export default {
    setup() {
        const title = ref('')
        const body = ref('')
        const tag = ref('')
        const tags = ref([])

        const router = useRouter()


        const addTag = () => {
           if(!tags.value.includes(tag.value)) {
            tag.value = tag.value.replace(/\s/, '')
            tags.value.push(tag.value)
           }
           tag.value = ''
        }


        const handleSubmit = async () => {
            const post = {
                title: title.value,
                body: body.value,
                tags: tags.value
            }
            await fetch('http://localhost:3000/posts', {
                method: 'POST',
                headers: {'content-type' : 'application/json'},
                body: JSON.stringify(post)
            })

            router.push('/')
        }
        

        return {title, body, tag, tags, addTag, handleSubmit}
    }
}
</script>

<style>
form {
    max-width: 480px;
    margin: 0 auto;
    text-align: left;
}
input, textarea {
    display: block;
    margin: 10px 0;
    width: 100%;
    border: 1px solid #eee;
    box-sizing: border-box;
    padding: 10px;
}
textarea {
    height: 160px;
}
label {
    display: inline-block;
    margin-top: 30px;
    position: relative;
    font-size: 20px;
    color: #fff;
    margin-bottom: 10px;
}
label::before {
    position: absolute;
    content: "";
    background: #ff8800;
    width: 100%;
    height: 100%;
    display: block;
    z-index: -1;
    padding-right: 40px;
    left: -30px;
    transform: rotateZ(-1.5deg);
}
button {
    display: block;
    background: #ff8800;
    color: #fff;
    padding: 10px; 
    border: none; 
    margin-top: 30px;
    border-radius: 5px;
}
.pill {
    color: #444;
    background: #ddd;
    margin: 10px 10px 0 0;
    padding: 8px;
    border-radius: 20px;
    display: inline-block;
    font-size: 14px;
}
</style>