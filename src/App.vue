<template>
  <v-app>
    <!-- <v-app-bar app flat>
      <Header />
    </v-app-bar> -->
    <v-main>
      <AccountManager />
    </v-main>
  </v-app>
</template>

<script>
import AccountManager from "./components/AccountManager";
import Header from "./components/Header";

export default {
  name: "App",

  components: {
    AccountManager,
    Header,
  },

  data: () => ({
    //
  }),
};
</script>
