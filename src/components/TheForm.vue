<template>
  <form @submit.prevent="handleSubmit">
    <div
      class="form-control"
      :class="{ invalid: validateUserName === 'invalid' }"
    >
      <label for="user-name">Your Name</label>
      <input
        id="user-name"
        name="user-name"
        type="text"
        v-model.trim="userName"
        @blur="validateName"
      />
      <p v-if="validateUserName === 'invalid'">Please enter the user name</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input
        v-model="userAge"
        id="age"
        name="age"
        type="number"
        ref="inputUserAge"
      />
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model="refferer">
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input
          id="interest-news"
          value="news"
          name="interest"
          type="checkbox"
          v-model="interest"
        />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input
          id="interest-tutorials"
          value="totorials"
          name="interest"
          type="checkbox"
          v-model="interest"
        />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input
          id="interest-nothing"
          name="interest"
          value="nothing"
          type="checkbox"
          v-model="interest"
        />
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>

    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input
          id="how-video"
          name="how"
          value="video"
          type="radio"
          v-model="learn"
        />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input
          id="how-blogs"
          name="how"
          value="blogs"
          type="radio"
          v-model="learn"
        />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input
          id="how-other"
          name="how"
          value="other"
          type="radio"
          v-model="learn"
        />
        <label for="how-other">Other</label>
      </div>
      <div class="form-control">
        <input
          type="checkbox"
          name="confirm"
          id="confirm"
          v-model="userConfirm"
        />
        <label for="confirm"> Agree to team ? </label>
      </div>
      <div class="form-control">
        <rating-control v-model="rating"></rating-control>
      </div>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>
<script>

import RatingControl from './RatingControl.vue';
export default {
  components: { RatingControl },

  data() {
    return {
      userName: '',
      userAge: null,
      refferer: 'wom',
      interest: [],
      learn: null,
      userConfirm: false,
       rating:null,
      validateUserName: 'pending',
    };
  },
  methods: {
    handleSubmit() {
      console.log(this.userName, 'Name');
      console.log(this.userAge, 'Age');
      console.log(this.refferer, 'Refferer');
      console.log(this.interest, 'interest ');
      console.log(this.learn, 'learn');
      console.log(this.$refs.inputUserAge.value, 'Age');
      console.log(this.userConfirm, 'userConfirm');
      console.log(this.rating, 'rating');
      (this.userAge = null),
        (this.userName = ''),
        (this.refferer = 'wom'),
        (this.interest = []),
        (this.learn = null),
        (this.userConfirm = false);
        this.rating = null
    },
    validateName() {
      if (this.userName === '') {
        this.validateUserName = 'invalid';
      } else {
        this.validateUserName = 'valid';
      }
    },
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

label {
  font-weight: bold;
}
.form-control.invalid input {
  border-color: red;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>