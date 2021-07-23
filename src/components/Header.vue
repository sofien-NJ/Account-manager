<template>
  <v-container>
    <div></div>
    <v-toolbar flat>
      <v-toolbar-title>
        <v-toolbar-items>
          <v-btn text><router-link to="/"> Profile </router-link></v-btn>

          <v-btn text><router-link to="About"> Favoris </router-link></v-btn>

          <v-btn text
            ><router-link to="Contact"> Adresse livraison </router-link>
          </v-btn>
        </v-toolbar-items></v-toolbar-title
      >

      <v-spacer></v-spacer>
    </v-toolbar>
  </v-container>
</template>

<script>
export default {
  name: "Header",

  data: () => ({}),
};
</script>
