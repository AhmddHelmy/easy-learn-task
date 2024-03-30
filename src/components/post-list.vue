<template>
    <div>
        <post-card v-for="post in posts" :key="post.id" :post="post" />
    </div>
</template>

<script>
import { Axios } from 'axios'
import PostCard from './PostCard.vue'

export default {
    components: {
        PostCard
    },
    data() {
        return {
            posts: []
        }
    },
    mounted() {
        Axios.get('https://jsonplaceholder.typicode.com/posts')
            .then(response => {
                this.posts = response.data
            })
            .catch(error => {
                console.error('Error fetching posts:', error)
            })
    }
}
</script>
