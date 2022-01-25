<template>
  <div id="app">
    <PostList />
    <AppPopUp 
      @closePopUpEvent="closePopUpEvent"
      @backPopUpEvent="backPopUpEvent"
      @continuePopUpEvent="continuePopUpEvent"
    />
    <AppButton 
      @appButtonClick="appButtonClick"
    />
    <Header
      @loginButtonClick="loginButtonClick"
    />
    <Footer />
    <LoginPopUp
      v-if="showLoginPopUp"
      @closePopUp="closePopUp"
    />
  </div>
</template>

<script>
import PostList from './components/PostList.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import LoginPopUp from './components/LoginPopUp.vue'

export default {
  name: 'App',
  components: {
    PostList,
    Header,
    Footer,
    LoginPopUp
  },

  data: () => ({
    showPopUpEvent: true,
    showLoginPopUp: false,


  }),

  computed: {

  },

  methods: {
    closePopUpEvent() {
      this.showPopUpEvent = false
      console.log('closePopUpEvent')
    },

    backPopUpEvent() {
      console.log('backPopUpEvent')
    },

    continuePopUpEvent() {
      console.log('continuePopUpEvent')
    },

    appButtonClick() {
      console.log('appButtonClick')
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
