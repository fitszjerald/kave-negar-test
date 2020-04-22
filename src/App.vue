<template>
  <v-app class="fonts">
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />
        <h2>تعرفه سرویس تماس آوانگار</h2>
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>
    <v-content>
      <avanegar />
    </v-content>
  </v-app>
</template>

<script>
import Avanegar from './components/Avanegar';

export default {
  name: 'App',

  components: {
    Avanegar
  },

  data: () => ({
    //
  }),
};

</script>
<style lang="scss" scoped>
@import "assets/scss/main.scss";

.fonts {
  font-family: "Vazir";
}
</style>