<template>
  <v-card class="mt-5" width="300" transition="fade-transition">
    <v-card-title class="d-flex justify-center">
      <h1 class="display-1">Register</h1>
    </v-card-title>
    <v-card-text>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          label="Email"
          prepend-icon="mdi-account-circle"
          v-model="email"
          :rules="emailRules"
          required
        />
        <v-text-field
          :type="showPassword ? 'text' : 'password'"
          label="password"
          prepend-icon="mdi-lock"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
          :rules="passwordRules"
          v-model="password"
          required
        />
        <v-text-field
          :type="showPassword ? 'text' : 'password'"
          label="repeat
        password"
          prepend-icon="mdi-lock"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
          :rules="password2Rules"
          required
        />
      </v-form>
    </v-card-text>
    <v-divider />
    <v-card-actions class="d-flex justify-end">
      <v-btn color="info" @click="validate">Register</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "Register",
  data() {
    return {
      showPassword: false,
      valid: true,
      password: "",
      passwordRules: [v => !!v || "password is required"],
      password2Rules: [v => v === this.password || "Passwords should match"],

      email: "",
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+/.test(v) || "E-mail must be valid"
      ]
    };
  },
  methods: {
    validate() {
      this.$refs.form.validate();
    }
  }
};
</script>
