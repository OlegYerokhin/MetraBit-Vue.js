<template>
  <div class="pop-up">

  <section class="autorization-section">
    <div class="content">
      <div class="tab-list" id="tab-list">
        <button 
          class="tab-btn"
          @click="signIn = true"
          :class="[signIn ? 'active-tab' : '']"
        >Sign In</button>
        <button 
          class="tab-btn"
          @click="signIn = false"
          :class="[!signIn ? 'active-tab' : '']"
        >Sign Up</button>
      </div>
      <keep-alive>
        <component :is="currentTab" />
      </keep-alive>
    </div>
  </section>
  <div class="pop-up-close">

      <button 
        class="cross-btn"
        @click="$emit('closePopUp')"
      >X</button>

    
  </div>
  </div>
</template>

<script>
export default {
  name: 'LoginPopUp',
  components: {
    LoginSignIn: () => import('./LoginSignIn.vue'),
    LoginSignUp: () => import('./LoginSignUp.vue'),
  },
  data: () => ({
    signIn: true
  }),
  computed: {
    currentTab() {
      if(this.signIn) {
        return 'LoginSignIn'
      }
      return 'LoginSignUp'
    }
  },
  
  
}
</script>

<style lang="scss" scoped>


.pop-up {
  position: fixed;
  background: #0008;
  z-index: 30;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.pop-up-close {
  position: absolute;
  z-index: 35;
  overflow: hidden;
  right: 430px;
  top: 135px;
  border: 2px solid rgb(2, 98, 128);
  border-radius: 50%;
  background-color: transparent;
  cursor: pointer;
}

.tab-btn {
    background-color: rgb(1, 118, 252);
    border-radius: 12px 12px 0 0;
    text-transform: uppercase;
    color: #fff;
    border: none;
    font-size: 20px;
    padding: 10px;
    width: 49.5%;
    cursor: pointer;
}

.active-tab {
    background-color: rgb(2, 98, 128);
}

.active {
    display: inline;
    border: 1px solid #000;
}

.tab-list {
    max-width: 50%;
    margin: 0 auto;
    margin-top: 5%;
    text-align: -webkit-center;
}

.cross-btn {
  font-weight: 700;
  font-family: cursive;
  color: red;
  
}


</style>