<template>
  <v-app class="overflow-hidden">
    <v-app-bar
      short
      app
      color="teal lighten-3"
      style="border-bottom: 2px solid rgba(0, 0, 0, 0.12)"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-btn @click="goto('/')"> <h2 class="heading">Vue Mart</h2></v-btn>
      <v-tabs align-with-title>
        <v-tab @click="goto('/')">Home</v-tab>
        <v-tab @click="goto('/men')">Mens</v-tab>
        <v-tab @click="goto('/women')">Women</v-tab>
        <v-tab @click="goto('/children')">Childrens</v-tab>
      </v-tabs>
      <v-spacer></v-spacer>
      <v-btn class="mx-2" fab dark large>
        <v-badge color="green" :content="items" :value="items">
          <v-icon>mdi-cart</v-icon>
        </v-badge>
      </v-btn>
    </v-app-bar>
    <router-view name="sidenav" />
    <v-main :class="'mini'">
      <router-view />
    </v-main>

    <Footer />
  </v-app>
</template>

<script>
import Footer from "../footer/Footer.vue";
export default {
  components: {
    Footer,
  },
  data() {
    return {
      links: [
        { title: "Home", link: "/" },
        { title: "Men", link: "/men" },
        { title: "Women", link: "/women" },
        { title: "Children", link: "/children" },
      ],
      drawer: false,
    };
  },
  methods: {
    goto(route) {
      this.$router.push(route);
    },
  },
};
</script>

<style lang="scss">
.routes {
  min-height: calc(100vh - 269px);
}
main {
  margin-left: 256px !important;
  &.mini {
    margin-left: 56px !important;
  }
}
</style>
