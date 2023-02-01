<template>
    <div>
        <WorkInProgress/>

        <!-- <PostList :posts="posts" :isLoading="isLoading" :pagination="pagination"/> -->
        <PostList/>
    </div>
</template>

<script>

import WorkInProgress from "../components/WorkInProgress.vue"
import PostList from "../components/posts/PostList.vue"

export default {
    name: 'App',
    components: {
        WorkInProgress,
        PostList
    }

}
</script>
