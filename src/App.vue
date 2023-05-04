<template>
  <base-card>
    <form @submit.prevent="validateTerms">
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
        <h4>Terms and Conditions</h4>
        <div class="input-group">
          <input id="terms" type="checkbox" v-model="terms" />
          <label for="terms"
            >I accept the terms and conditions for signing up to this service,
            and hereby confirm I have read the privacy policy.</label
          >
          <p class="error-title" v-if="!terms" ref="termCheck"></p>
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
      terms: false,
    };
  },
  methods: {
    checkValidation(e, inputName, value) {
      if (!value) {
        e.target.classList.add("error-bordered");
        e.target.nextSibling.nextSibling.textContent = `Please enter ${inputName}`;
      } else {
        e.target.classList.remove("error-bordered");
        e.target.nextSibling.nextSibling.textContent = "";
      }
    },
    validateTerms() {
      if (!this.terms) {
        this.$refs.termCheck.style.fontWeight = "bold";
        this.$refs.termCheck.textContent =
          "Please accept our terms to continue...";
      }
    },
  },
};
</script>

<style scoped></style>
