<template>
  <div id="app">
    <Header 
      @loginButtonClick="loginButtonClick"
      :showLoginPopUp.sync="showLoginPopUp"
    />
    <PostList />
    <LoginPopUp
      v-if="showLoginPopUp"
      :showLoginPopUp.sync="showLoginPopUp"
    />
  </div>
</template>

<script>
import PostList from './components/PostList.vue'
import Header from './components/Header.vue'
import LoginPopUp from './components/LoginPopUp.vue'

export default {
  name: 'App',
  
  components: {
    PostList,
    Header,
    LoginPopUp
  },
  data: () => ({
    showPopUpEvent: true,
    showLoginPopUp: false,
  }),
  methods: {
    closePopUpEvent() {
      this.showPopUpEvent = false
      console.log('closePopUpEvent')
    },

    loginButtonClick() {
      this.showLoginPopUp = true
    },

    closePopUp() {
      this.showLoginPopUp = false
    },
  }
}
</script>

<style>

</style>
