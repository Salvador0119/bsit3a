<template>
  <v-app dark>
    <v-navigation-drawer
    dark
    color="primary"
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
        <v-list-item>
          <v-icon left>mdi-account-school</v-icon>
 

          <v-list-item-content>
            <v-list-item-title>BSIT3A</v-list-item-title>
            <v-list-item-subtitle>Logged In</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

      <v-list>
        <v-subheader>Main Navigation</v-subheader>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <template v-slot:append>
        <div class="pa-2"><v-btn color="black" block to="/"><v-icon left>mdi-logout</v-icon>LOGOUT</v-btn>
        </div>
      </template>


      <v-list>
        <v-list-item
          v-for="(newPage, i) in newPage"
          :key="i"
          :to="newPage.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ newPage.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ newPage.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      

    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app color="primary">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" color="white" />

      <v-spacer />
      <v-toolbar-title style="color: white">{{ title }}</v-toolbar-title>
      <v-spacer />

    </v-app-bar>

    <v-main>

        <Nuxt />
    
    </v-main>
  </v-app>
</template>
  
<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
  
      ],
      newPage: [
        {
          icon: "mdi-view-list",
          title: "Dashboard",
          to: "/dashboard",
        },
        {
          icon: "mdi-view-list",
          title: "Student List",
          to: "/studentinfo",
        },

      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "BSIT 3A",
    };
  },
};
</script>
<style scoped>
.profile {
  background: "primary"
}
</style>

  