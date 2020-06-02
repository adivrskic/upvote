<template>
    <div class="container">
        <div v-for="post in postData" :key="post.title">
            <Post 
                @upvote="orderPosts"
                :title="post.title"
                :content="post.content"
                :submitted_by="post.submitted_by"
                :votes="post.votes" 
                :hex="post.hex"
            />
        </div>
    </div>
</template>

<script>
import postData from '../data.json'

import Post from './Post'

export default {
    data() {
        return {
            postData
        }
    },
    components: {
        Post
    },
    methods: {
        orderPosts(data) {
            this.postData.forEach(item => {
                if(item.title == data.title) {
                    item.votes = data.votes;
                }
            })

            this.postData.sort(function(a,b) {
                return (a.votes < b.votes ? 1 : ((a.votes > b.votes) ? -1 : 0));
            });
        }
    }
}
</script>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    width: 40rem;
    max-width: 100%;
    margin: 0 auto;
    padding: 1rem;
}
</style>