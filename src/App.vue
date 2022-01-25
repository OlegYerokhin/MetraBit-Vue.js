<template>
  <div id="app">
    <AppButton 
      appButtonText = Save
    />
    <PostList />
    
  </div>
</template>

<script>
import PostList from './components/PostList.vue'
import AppButton from './components/AppButton.vue'

export default {
  name: 'App',
  components: {
    PostList,
    AppButton,
  },
  data: () => ({

  }),
}
</script>

<style>

</style>
