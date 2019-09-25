<template>
  <v-app>
    <v-app-bar app color="deep-purple" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vue PWA Experiments</v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer
      temporary
      app
      dark
      color="deep-purple"
      v-model="drawer"
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">Experiments</v-list-item-title>
          <v-list-item-subtitle>Menu</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider color="white"></v-divider>

      <v-list nav>
        <v-list-item v-for="item in items" :key="item.title" link :to="item.to">
          <v-list-item-icon>
            <v-icon>mdi-{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <v-container>
        <router-view></router-view>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      drawer: false,
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: '/'
        },
        {
          title: 'Camera',
          icon: 'camera',
          to: '/camera'
        },
        {
          title: 'QR Code',
          icon: 'qrcode-scan',
          to: '/qrcode'
        }
      ]
    };
  }
};
</script>
