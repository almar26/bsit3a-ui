<template>
  <div class="d-flex align-center justify-center" style="height: 100vh">
    <v-card width="450" class="mx-auto card-border" outlined>
      <v-img src="logo.png" max-height="130" contain></v-img>

      <v-row class="mx-12 mt-1">
        <v-col cols="auto" class="mr-auto">
          <v-btn outlined color="blue-grey"
            ><v-icon color="red" left>mdi-google</v-icon> Google</v-btn
          >
        </v-col>
        <v-col cols="auto">
          <v-btn outlined color="blue-grey"
            ><v-icon color="blue" left>mdi-facebook</v-icon> Facebook</v-btn
          >
        </v-col>
      </v-row>
      <div class="hr-sect mx-15 my-5">or sign up with</div>
      <v-form ref="form" v-model="valid" lazy-validation class="mx-15">
        <v-text-field
          v-model="name"
          :rules="nameRules"
          label="Name"
          prepend-inner-icon="mdi-account"
          outlined
          required
        ></v-text-field>
        <v-text-field
          v-model="email"
          :rules="emailRules"
          label="E-mail"
          prepend-inner-icon="mdi-email"
          outlined
          required
        ></v-text-field>
        <v-text-field
          v-model="password"
          :rules="passwordRules"
          label="Password"
          type="password"
          prepend-inner-icon="mdi-lock"
          outlined
          required
        ></v-text-field>
        <v-btn :disabled="!valid" color="primary" block @click="submit">
          Sign Up
        </v-btn>
      </v-form>

      <v-card-actions class="mb-5 mt-3 text-center">
        <v-spacer></v-spacer>
        <span class="mr-2">
          Already have an Account?
          <NuxtLink to="/" class="nuxt-link">Sign In</NuxtLink></span
        >
        <v-spacer></v-spacer>
      </v-card-actions>
    </v-card>

    <v-snackbar v-model="snackbar" top color="green" tile>
      Successfully Submited

      <template v-slot:action="{ attrs }">
        <v-btn icon v-bind="attrs" @click="snackbar = false">
          <v-icon>mdi-close</v-icon>
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  layout: "auth",
  data() {
    return {
      snackbar: false,
      valid: true,
      name: "",
      email: "",
      password: "",
      nameRules: [(v) => !!v || "Name is required"],
      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
      ],
      passwordRules: [(v) => !!v || "Password is required"],
    };
  },
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        console.log("Successfully Login");
        // this.$router.push('/register');
        this.$refs.form.reset();
        this.snackbar = true
      }
    },
  },
};
</script>
<style scoped>
.nuxt-link {
  text-decoration: none;
  padding-top: 5px;
}
.card-border {
  border-radius: 20px;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
.hr-sect {
  display: flex;
  flex-basis: 100%;
  align-items: center;
  color: rgba(0, 0, 0, 0.9);
  margin: 8px 0;
}
.hr-sect::before,
.hr-sect::after {
  content: "";
  flex-grow: 1;
  background: rgba(0, 0, 0, 0.15);
  height: 1px;
  font-size: 0;
  line-height: 0;
  margin: 0 8px;
}
</style>