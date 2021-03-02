<template>
  <v-app style="-webkit-app-region: drag">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant.sync="mini"
      permanent
      dark
      color="#272F34"
      app
    >
      <v-list-item class="px-2 pt-1">
        <v-list-item-avatar>
          <v-img src="@/assets/avatar.jpeg" alt="admin" class="mx-auto"></v-img>
        </v-list-item-avatar>
        <v-list-item-title class="ml-4 text-capitalize">Admin Name</v-list-item-title>
      </v-list-item>
      <v-list shaped class="clickable">
        <v-list-item-group
        v-model="model"
        active-class="border"
        color="orange"
      >
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to=item.route
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon"></v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title v-text="item.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="#272F34" dark>
      <v-app-bar-nav-icon
        @click.stop="mini = !mini"
        class="clickable"
      ></v-app-bar-nav-icon>
      <v-toolbar-title>Parking Admin</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon class="clickable">
        <v-icon>mdi-logout</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-container class="scroll-y" fluid>
        <v-row align="center" justify="center"  style="background: #EEEEEE;">
          <router-view style=" height: 100vh"></router-view>
        </v-row>
      </v-container>
    </v-main>
    <v-btn
      v-scroll="onScroll"
      bottom
      right
      color="#272F34"
      dark
      fab
      fixed
      small
      @click="toTop"
      class="clickable"
    >
     <v-icon dark>
        mdi-chevron-up
      </v-icon>
    </v-btn>
  </v-app>
</template>

<script>
export default {
  name: "App",
  props: {
    source: String,
  },
  components: {},

  data: () => ({
    drawer: null,
    mini: false,
    fab: false,
    items: [
      { icon: "mdi-home", text: "Home", route: "/" },
      { icon: "mdi-cog", text: "Settings", route: "/settings" },
      { icon: "mdi-chart-bar", text: "Statistics", route: "/statistics" },
      { icon: "mdi-history", text: "History", route: "/history" },
    ],
    model: 1
  }),
  methods: {
    onScroll(e) {
      if (typeof window === "undefined") return;
      const top = window-pageYOffset || e.target.scrollTop  || 0;
      this.fab = top > 20
    },
    toTop(){
      this.$vuetify.goTo(0);
      console.log(this.$route)
    }
  },
};
</script>
<style lang="scss">
.clickable {
  -webkit-app-region: no-drag;
}
::-webkit-scrollbar{
  width: 12px;
}
::-webkit-scrollbar-track{
  box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
  background: #272f3479;
}
::-webkit-scrollbar-thumb{
  
  box-shadow: inset 0 0 6px rgba(0,0,0,0.5);
  background: #272F34;
}
.orange{
  background: #F9AA33;
}
</style>
