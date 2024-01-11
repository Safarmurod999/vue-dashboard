<template>
  <v-navigation-drawer v-model="getDrawer" app>
    <v-sheet color="grey-lighten-4" class="pa-4 text-center">
      <v-avatar class="mb-4" color="grey-darken-1" size="64"></v-avatar>
      <div>Dashboard</div>
    </v-sheet>
    <v-divider></v-divider>
    <v-list>
      <v-list-item
        v-for="[icon, text] in links"
        :key="icon"
        :prepend-icon="icon"
        :title="text"
        link
      ></v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
<script setup>
const links = [
  ["mdi-view-dashboard", "Dashboard"],
  ["mdi-account", "Profile"],
  ["mdi-clipboard-list-outline", "Products"],
  ["mdi-clipboard-list-outline", "Order"],
  ["mdi-cogs", "Settings"],
];
</script>
<script>
export default {
  props:{
    drawer:{
      type:Boolean,
      required:true,
    }
  },
  name: "SidebarVue",
  computed: {
    getDrawer() {
      return this.drawer;
    },
  },
};
</script>
<style></style>
