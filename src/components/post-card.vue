<template>
    <div class="card m-2" style="width: 18rem;">
        <img :src="'https://picsum.photos/600/300/?image=' + post.id" class="card-img-top" alt="Post Image">
        <div class="card-body">
            <h5 class="card-title">{{ post.title }}</h5>
            <p class="card-text">User: {{ user.name }}</p>
            <p class="card-text">Phone: {{ user.phone }}</p>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    props: ['post'],
    data() {
        return {
            user: {}
        }
    },
    mounted() {
        axios.get(`https://jsonplaceholder.typicode.com/users/${this.post.userId}`)
            .then(response => {
                this.user = response.data
            })
            .catch(error => {
                console.error('Error fetching user details:', error)
            })
    }
}
</script>
