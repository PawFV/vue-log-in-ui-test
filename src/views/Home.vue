<template
  ><div class="home mx-auto">
    <v-tabs class="d-flex justify-center">
      <v-tab @click="toggleTab = 'login'">Login</v-tab>
      <v-tab @click="toggleTab = 'register'">Register</v-tab>
    </v-tabs>

    <login v-show="toggleTab === 'login'" class="mx-auto"></login>
    <register v-show="toggleTab === 'register'" class="mx-auto"></register>
  </div>
</template>

<script>
import Login from "@/components/Login";
import Register from "@/components/Register";
export default {
  components: {
    Login,
    Register
  },
  data: () => ({
    toggleTab: "login"
  })
};
</script>

<style scoped>
.home h1 {
  text-align: center;
}
</style>
