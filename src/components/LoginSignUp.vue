<template>
  <div>
    <div class="sign-up">
      <div>
        <form 
          @submit.prevent="checkForm($event)"
        >
          <input 
            @change="checkLogin()"
            v-model.trim="login"
            type="text"
            id="existing-login"
            name="login"
            placeholder="Enter your login"          
          />

          <input 
            @change="checkPassword()"
            v-model="password"
            type="password" 
            id="existing-password"
            name="password"
            placeholder="Enter your password"
          />

          <input
            v-model="repeatedPassword" 
            @change="repeatedPassword()"
            type="password"
            id="repeated-password"
            class="password"
            name="password"
            placeholder="Repeat your password"
          />

          <input 
            type="submit" 
            class="sign-up-btn"
            value="Sign Up"
            id="sign-up-btn"
            @click="showMessage()"
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
  name: 'LoginSignUp',
  props: {
    usersUsernames: {
      type: Array,
      default: () => []
    }
  },
  data: () => ({
    login: '',
    password: '',
    repeatedPassword: '',
    message: '',
    error: '',
    showInfoMessage: false
  }),
  methods: {
    checkForm(event) {
      if(this.login && 
        this.password &&
        this.repeatedPassword &&
        this.password === this.repeatedPassword &&
        this.usersUsernames.indexOf(this.login) === -1) {
        this.message = 'You have successfully registered!'
      }
      if(this.password !== this.repeatedPassword) {
        this.error = 'You entered different passwords. Please edit them and try again'
      }
      event.preventDefault()
    },

    checkLogin() {
      if(!this.login) {
        this.error = 'Enter your login please!'
      }

      if(this.usersUsernames.indexOf(this.login) !== -1) {
        this.error = 'User with this login exists'
      }
    },

    checkPassword() {
      if(!this.password) {
        this.error = 'Wrong password. Try again!'
      }
    },

    checkRepeatedPassword() {
      if(!this.repeatedPassword) {
        this.error = 'Please enter your password again'
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

body {
  text-align: -webkit-center;
}

form {
  padding: 20px;
  background-color: #fff;
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

.sign-up-btn {
  background-color: rgb(1, 118, 252);
  border-radius: 7px;
  max-width: 25%;
  border: 1px solid #000;
  color: #fff;
  cursor: pointer;
  text-transform: uppercase;
}

.sign-up-btn:hover {
  background-color: rgb(2, 98, 128);
  transition: 0.5s linear;
}
</style>