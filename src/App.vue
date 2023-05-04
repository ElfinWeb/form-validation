<template>
  <base-card>
    <form>
      <div class="row">
        <h4>Account</h4>
        <div class="input-group input-group-icon">
          <input
            type="text"
            placeholder="Full Name"
            @focusout="checkValidation($event, 'Full Name', fullName)"
            v-model="fullName"
          />
          <div class="input-icon"><i class="fa fa-user"></i></div>
          <p class="error-title" v-if="!fullName"></p>
        </div>
        <div class="input-group input-group-icon">
          <input
            type="email"
            placeholder="Email Adress"
            @focusout="checkValidation($event, 'Email', email)"
            v-model="email"
          />
          <div class="input-icon"><i class="fa fa-envelope"></i></div>
          <p class="error-title" v-if="!email"></p>
        </div>
        <div class="input-group input-group-icon">
          <input
            type="password"
            placeholder="Password"
            @focusout="checkValidation($event, 'Password', password)"
            v-model="password"
          />
          <div class="input-icon"><i class="fa fa-key"></i></div>
          <p class="error-title" v-if="!password"></p>
        </div>
      </div>
      <div class="row">
        <div class="col-half">
          <h4>Date of Birth</h4>
          <div class="input-group">
            <div class="col-third">
              <input type="text" placeholder="DD" />
            </div>
            <div class="col-third">
              <input type="text" placeholder="MM" />
            </div>
            <div class="col-third">
              <input type="text" placeholder="YYYY" />
            </div>
          </div>
        </div>
        <div class="col-half">
          <h4>Gender</h4>
          <div class="input-group">
            <input id="gender-male" type="radio" name="gender" value="male" />
            <label for="gender-male">Male</label>
            <input
              id="gender-female"
              type="radio"
              name="gender"
              value="female"
            />
            <label for="gender-female">Female</label>
          </div>
        </div>
      </div>
      <div class="row">
        <h4>Terms and Conditions</h4>
        <div class="input-group">
          <input id="terms" type="checkbox" />
          <label for="terms"
            >I accept the terms and conditions for signing up to this service,
            and hereby confirm I have read the privacy policy.</label
          >
        </div>
      </div>
      <button class="submit-button" type="submit">Submit</button>
    </form>
  </base-card>
</template>

<script>
import BaseCard from "./components/UI/BaseCard.vue";
export default {
  components: {
    BaseCard,
  },
  data() {
    return {
      fullName: "",
      email: "",
      password: "",
      gender: "",
      terms: false,
      birthDay: "",
      birthMonth: "",
      birthYear: "",
    };
  },
  methods: {
    checkValidation(e, inputName, value) {
      if (!value) {
        e.target.classList.add("error-bordered");
        e.target.nextSibling.nextSibling.textContent = `Please enter ${inputName}`;
        console.log(inputName);
        console.log(value);
      } else {
        e.target.classList.remove("error-bordered");
        e.target.nextSibling.nextSibling.textContent = "";
      }
    },
  },
};
</script>

<style scoped></style>
