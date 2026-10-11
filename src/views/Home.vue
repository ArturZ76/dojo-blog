<template>
    <div>
        <h1>Home</h1>

        <div v-if="error">{{ error }}</div>
        <div v-if="posts.length">
            <PostList v-if="showPost" :posts="posts" />
        </div>
        <div v-else>Loading...</div>
        <button @click="showPost = !showPost">Toggle post</button>
        <button @click="posts.pop()">Delete Post</button>
    </div>
</template>

<script>
import PostList from '@/components/PostList.vue';
import { ref } from 'vue'
import getPosts from '@/composables/getPosts';

export default {
    name: "Home",
    components: { PostList },
    setup() {
        const showPost = ref(true)
        const { posts, error, load } = getPosts()
        load()
        return { posts, showPost, error }
    }
}

</script>

<style></style>