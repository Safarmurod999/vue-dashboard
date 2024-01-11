<template>
  <v-app-bar scroll-behavior="elevate">
    <v-app-bar-nav-icon @click="$emit('handleDrawer')"></v-app-bar-nav-icon>
    <v-spacer/>
    <v-col lg="6" cols="12" >
      <v-form >
        <v-text-field rounded outlined dense/>
      </v-form>
    </v-col>
    <v-spacer/>
    <template v-slot:append>
      <v-btn icon="mdi-heart"></v-btn>

      <v-btn icon="mdi-magnify"></v-btn>

      <v-btn icon="mdi-dots-vertical"></v-btn>
    </template>
  </v-app-bar>
</template>
<script>
export default {
    name:'HeaderVue'
};
</script>
<style></style>
