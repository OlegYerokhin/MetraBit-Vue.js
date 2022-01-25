<template>
  <div>
    <div class="sign-in">
      <div class="active">
        <form 
          @submit.prevent="checkForm($event)"
        >
          <input 
            @change="checkLogin()"
            v-model.trim="login"
            type="text"
            id="existing-login"
            name="login"
            placeholder="Login"
          />

          <input 
            @change="checkPassword()"
            v-model="password"
            type="password" 
            id="existing-password"
            name="password"
            placeholder="Password"
          />

          <input 
            @click="showMessage()"
            type="submit" 
            class="sign-in-btn"
            value="Sign In"
            id="sign-in-btn"
          />

          <div v-if="showInfoMessage === true">
            <div  
              v-if="!message.length"
              class="red"
            >
              {{ error }}
            </div>
            <div 
              v-else
              class="green"
            >
              {{ message }}
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginSignIn',
  data: () => ({
    login: '',
    password: '',
    message: '',
    error: '',
    showInfoMessage: false
  }),
  methods: {
    checkForm(event) {
      if(this.login && 
        this.password) {
        this.message = `Congratulations! You have successfully logged in as user ${this.login}`
      }
      event.preventDefault()
    },

    checkLogin() {
      if(!this.login) {
        this.error = 'Enter your login please!'
      }
    },

    checkPassword() {
      if(!this.password) {
        this.error = 'Wrong password. Try again!'
      }
    },

    showMessage() {
      this.showInfoMessage = true
    }
  }
}
</script>

<style lang="scss" scoped>

.red {
    background-color: red;
    color: #fff;
    text-align: center;
    margin: 15px auto;
    border-radius: 20px;
    max-width: 50%;
    padding: 5px;
    border: 1px solid black;
}

.green {
    background-color: lightgreen;
    text-align: center;
    margin: 15px auto;
    border-radius: 20px;
    max-width: 50%;
    padding: 5px;
    border: 1px solid black;
}

form {
  background-color: #fff;
  padding: 20px;
  width: 47%;
  margin: 0 auto;
  font-size: 22px;
  text-align: -webkit-center
}

input {
  display: block;
  width: 70%;
  height: 35px;
  margin: 15px;
  border: none;
  border-bottom: 1px solid #000;
  font-size: 20px;
}

.sign-in-btn {
  background-color: rgb(1, 118, 252);
  border-radius: 7px;
  max-width: 25%;
  border: 1px solid #000;
  color: #fff;
  cursor: pointer;
  text-transform: uppercase;
  justify-content: center;
}

.sign-in-btn:hover {
  background-color: rgb(2, 98, 128);
  transition: 0.5s linear;
}
</style>