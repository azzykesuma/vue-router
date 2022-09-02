<template>
  <div class="home">
    <div v-if="posts.length">
      <PostLists :posts='posts'/>
    </div>
    <div v-else>loading...</div>
    <div v-if="error">{{ error }}</div>
  </div>
</template>

<script>
import GetPost from '../composable/GetPost'
import { ref, reactive } from '@vue/reactivity'
import { computed } from '@vue/runtime-core'
import PostLists from '../components/PostLists.vue'
// @ is an alias to /src

export default {
  name: 'HomeView',
  components : { PostLists },
  setup() {
    // template refs

    // wrapping the variable in ref will make the
    // // value reactive/can be changed
    // const ninjaOne = ref({
    //   name : 'mario',
    //   age : 35
    // })

    // const updateNinjaOne = () => {
    //   ninjaOne.value.age = 40
    // }

    // // computed
    // const names = ref(['azzy', 'mario', 'luigi'])
    // const search = ref('')
    // // the compute function called to compute/manipulate data
    // const matchingSearch = computed(() => {
    //   return names.value.filter(name => name.includes(search.value))
    // })
    
    // fetching data
    const { error, load, posts} = GetPost()
    load()

      return {
        posts,
        error
    }
  }
}
</script>
