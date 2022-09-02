<template>
  <div class="postLists">
    <div v-for="post in posts" :key='post.id'>
        <SinglePost :post='post'/>
    </div>
  </div>
</template>

<script>
import { onMounted, onUnmounted } from '@vue/runtime-core'
import SinglePost from './SinglePost.vue'

export default {
    props : ['posts'],
    components : {SinglePost},
    setup(props) {
        onMounted(() => {
            console.log(`component mounted`)
        })
        onUnmounted(() => {
             console.log(`component unmounted`)
        })
    } 
}
</script>

<style>

</style>