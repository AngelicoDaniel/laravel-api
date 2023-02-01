<template>
    <div>
        <WorkInProgress/>

        <PostList :posts="posts" :isLoading="isLoading"/>
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
    },
    data(){
        return{
            posts: [],
            isLoading: false,
            pagination: {}
        }
    },
    mounted(){
        this.getPosts();
    },
    methods: {
        getPosts(page = 1){
            this.isLoading = true
            axios.get('http://127.0.0.1:8000/api/posts?page' + page)
                .then(res => {
                    console.log(res.data);
                    // this.posts = res.data.data

                    //destrutturizzazione
                    const { data, current_page, last_page} = res.data;

                    this.posts = data;
                    this.pagination = {
                        lastPage: last_page,
                        currentPage: current_page
                    }


                }).catch(err =>{
                    console.log(err)
                }).then(() =>{
                    this.isLoading = false
                })
        }
    }

}
</script>
