<template>
    <div class="post-container">
        <div class="post-icon" :style="hex">
            <Icon />
        </div>
        <div class="post-data">
            <h3>{{ title }}</h3>
            <p class="post-content">{{ content }}</p>
            <p class="post-small">Submitted By: {{ submitted_by }}</p>
        </div> 
        <div class="post-votes"
             @click="addVote(title)"
        >
            &#8963; {{ numVotes }}
        </div>
    </div>
</template>

<script>
import Icon from '../assets/Icon'

export default {
    data() {
        return {
            numVotes: this.$props.votes
        }
    },
    components: {
        Icon
    },
    props: [
        'title',
        'content',
        'submitted_by',
        'votes',
        'hex'
    ],
    methods: {
        addVote(title) {
            this.$emit('upvote', {
                'title': title,
                'votes': this.numVotes++ 
            } )
        }
    }
}
</script>

<style scoped>
.post-container {
    display: flex;
    flex-direction: row;
    width: 100%;
    border: 1px solid #ddd;
    margin-bottom: 1rem;
    padding: 1rem;
}

h3 {
    margin: 0;
    text-transform: capitalize;
}

.post-icon {
    position: relative;
}

.post-icon {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 3rem;
    height: 3rem;
    margin-right: 1rem;
}

.post-icon svg {
    position: absolute;
    width: 70%;
}

.post-content {
    font-size: .875rem;
    text-transform: lowercase;
}

.post-small {
    font-size: .75rem;
    text-transform: lowercase;
}

.post-data {
    width: 90%;
}

.post-votes {
    width: 10%;
    display: flex;
    align-items: center;
    cursor: pointer;
}
</style>