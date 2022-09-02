<template>
  <h1>detail</h1>
  <div v-if="error">
    <p>error loading data</p>
  </div>
    <div v-if="post">
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
        <span v-for="tag in post.tags" :key="tag">
            #{{ tag }}
        </span>
    </div>
</template>

<script>
import { useRoute } from 'vue-router';
import GetSinglePost from '../composable/GetSinglePost'

export default {
    props : ['id'],
    setup(props) {
        // getting params manually
        const route = useRoute()
        const id = route.params.id

        const { load, post, error } = GetSinglePost(id);
        
        load();

        return {post, error}
    }
}
</script>

<style>

</style>