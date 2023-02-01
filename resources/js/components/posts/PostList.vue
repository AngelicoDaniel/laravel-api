<template>
        <div>
            <Loader v-if="isLoading"/>

            <ul v-else-if="posts.length">
                <li v-for="elem in posts" :key="elem.id">{{ elem.title }}</li>
            </ul>
            <p v-else>Non ci sono post nel DB</p>
        </div>
</template>

<script>
import Loader from '../Loader.vue'

export default {
    name: 'PostList',
    props: ['posts', 'isLoading'],
    components: {
        Loader,
    }
}
</script>

