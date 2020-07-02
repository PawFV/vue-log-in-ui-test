<template>
  <v-card class="mt-5" width="300">
    <v-card-title class="d-flex justify-center">
      <h1 class="display-1">Login</h1>
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
          required
        />
      </v-form>
    </v-card-text>
    <v-divider />
    <v-card-actions class="d-flex justify-end">
      <v-btn color="info" @click="validate">Login</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      showPassword: false,
      valid: true,
      passwordRules: [v => !!v || "password is required"],
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

<style scoped>
h1 {
  text-align: center;
}
</style>
