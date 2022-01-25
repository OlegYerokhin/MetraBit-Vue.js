<template>
  <div class="sign-up-page">
    <h3 class="sign-up-page__title">Sign Up</h3>
    <form class="sign-up-page__form">
      
      <div>
        <label for="name">Name:</label>
        <input 
          id="name"
          v-model.lazy="userInfo.name" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'name' }" 
          @focus="setActiveItem('name')" 
        />
      </div>

      <div>
        <label for="surname">Surname: </label>
        <input 
          id="surname"
          v-model.lazy="userInfo.surname" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'surname' }" 
          @focus="setActiveItem('surname')" 
        />
      </div>

      <div>
        <label for="email">Email:</label>
        <input  
          id="email"
          v-model.trim="userInfo.email" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'email' }"
          @focus="setActiveItem('email')" 
        />
      </div>

      <div>
        <label for="phone">Phone:</label>
        <input 
          id="phone" 
          v-model.number="userInfo.phone" 
          type="number" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'phone' }" 
          @focus="setActiveItem('phone')"
        />
      </div>

      <div>
        <label for="birth">Birth year:</label>
        <input 
          id="birth"
          v-model.number="userInfo.birthYear" 
          type="number" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'birthYear' }" 
          @focus="setActiveItem('birthYear')" 
        />
      </div>

      <div class="gender">
        <label for="male-gender">Male</label>
        <input 
          id="male-gender" 
          v-model="userInfo.gender" 
          type="radio" 
          value="male" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'gender' }"
          @focus="setActiveItem('gender')" 
        />
        
        <label for="female-gender">Female</label>
        <input 
          id="female-gender" 
          v-model="userInfo.gender" 
          type="radio" 
          value="female" 
          class="sign-up-page__form-item" 
        />
      </div>

      <div>
        <label for="login">Login:</label>
        <input 
          id="login" 
          v-model.trim="userInfo.logIn" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'logIn' }" 
          @focus="setActiveItem('logIn')"
        />  
      </div>

      <div>
        <label for="pass">Password:</label>
        <input 
          id="pass"
          v-model.trim="userInfo.password" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'password' }" 
          @focus="setActiveItem('password')" 
        />
      </div>

      <div>
        <label for="repeatedPass">Repeat password:</label>
        <input 
          id="repeatedPass"
          v-model.trim="userInfo.repeatedPassword" 
          type="text" 
          class="sign-up-page__form-item" 
          :class="{ active: isActive === 'repeatedPassword' }"
          @focus="setActiveItem('repeatedPassword')"  
        />
      </div>

      <div>
        <label for="commercial">Commercial experience:</label>
        <input 
          id="commercial"
          v-model="userInfo.commercialExperience" 
          type="checkbox" 
          true-value="Yes, I have" 
          false-value="No, I haven't" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'commercialExperience' }" 
          @focus="setActiveItem('commercialExperience')" 
        />
      </div>

      <div v-show="userInfo.commercialExperience === 'Yes, I have'">
        <label for="yearsOfExp">How many years do you have?</label>
        <input 
          id="yearsOfExp"
          v-model="userInfo.yearsOfExperience"
          type="number" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'yearsOfExperience' }" 
          @focus="setActiveItem('yearsOfExperience')" 
        />
      </div>

      <div>
        <label for="country">Country:</label>
        <input 
          id="country" 
          v-model.lazy="userInfo.country" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'country' }" 
          @focus="setActiveItem('country')"
        />
      </div>

      <div>
        <label for="city">City:</label>
        <input 
          v-if="userInfo.country !== 'Ukraine'" 
          id="city"
          v-model="userInfo.city" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'city' }" 
          @focus="setActiveItem('city')" 
        />

        <select 
          v-else
          v-model="userInfo.city" 
        >
          <option disabled value="">Choose your city</option>
          <template v-for="(city, index) in ukrainianCities">
            <option :key="index">
              {{ city }}
            </option>
          </template>
        </select>
      </div>

      <div>
        <label for="address">Address:</label>
        <input 
          id="address"
          v-model="userInfo.address" 
          type="text" 
          class="sign-up-page__form-item"
          :class="{ active: isActive === 'address' }" 
          @focus="setActiveItem('address')" 
        />
      </div>

      <div>
        <label for="englishLabel">English level:</label>
        <select 
          id="englishLevel"
          v-model="userInfo.englishLevel" 
        >
          <option disabled value="">Choose your level</option>
          <template 
            v-for="(value, index) in englishLevelsValues"
          >
            <option 
              v-bind="value" 
              :key="`${index} + ${value}`"
            ></option>
          </template>
        </select>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'SignUp',
  data: () => ({
    userInfo: {
      name: '',
      surname: '',
      email: '',
      phone: null,
      birthYear: null,
      gender: null,
      logIn: '',
      password: '',
      repeatedPassword: '',
      commercialExperience: null,
      yearsOfExperience: null,
      country: '',
      city: '',
      address: '',
      englishLevel: '',
    },
    ukrainianCities: ['Vinnytsia', 
      'Kropyvnytskyi', 
      'Poltava', 
      'Kharkiv', 
      'Dnipro', 
      'Luhansk', 
      'Kherson', 
      'Donetsk', 
      'Lutsk', 
      'Simferopol', 
      'Khmelnitsky', 
      'Zhitomir', 
      'Lviv', 
      'Sumy', 
      'Cherkasy', 
      'Zaporizhya', 
      'Mykolaiv', 
      'Ternopil', 
      'Chernihiv', 
      'Ivano-Frankivsk', 
      'Odesa', 
      'Uzhgorod', 
      'Chernivtsi', 
      'Kyiv'],
    englishLevelsValues: [
      {
        value: 'A1',
        label: 'Beginner'
      },
      {
        value: 'A2',
        label: 'Elementary'
      },
      {
        value: 'B1',
        label: 'Intermediate'
      },
      {
        value: 'B2',
        label: 'Upper Intermediate'
      },
      {
        value: 'C1',
        label: 'Advanced'
      },
      {
        value: 'C2',
        label: 'Proficiency'
      }
    ],
    isActive: '',

  }),
  methods: {
    setActiveItem(activeInput) {
      this.isActive = activeInput
    }
  }
}
</script>

<style lang="scss" scoped>
.sign-up-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  input {
    padding: 8px 12px;
    border: 1px solid #000;
    border-radius: 20px;
    font-size: 16px;
  }
  .gender {
    display: flex;
    justify-content: center;
  }

  select {
    padding: 8px 12px;
    border: 1px solid #000;
    border-radius: 20px;
    font-size: 16px;
    width: 220px;
  }

  label {
    display: block;
  }

  div {
    margin-top: 10px;
  }

  .sign-up-page__form-item.active {
    background-color: lightgrey;
  }

  
}




</style>