<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
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
          :href="text.toLowerCase()=='dashboard'?'/':text.toLowerCase()"
          link="true"
        ></v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <!-- <HeaderVue @handleDrawer="drawer = !drawer" /> -->
      <v-app-bar scroll-behavior="elevate">
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
        <v-spacer />
        <v-col lg="4" cols="4" style="border: none">
          <v-form style="border: none">
            <v-text-field
              :loading="loading"
              variant="outlined"
              density="compact"
              hide-details="auto"
              append-inner-icon="mdi-magnify"
              clearable
              single-line
              @click:append-inner="onClick"
              label="Search..."
            />
          </v-form>
        </v-col>
        <v-spacer />
        <v-menu transition="slide-y-transition">
          <template v-slot:activator="{ props }">
            <v-btn v-bind="props"
              ><v-badge content="5" color="error"
                ><v-icon size="25">mdi-bell-outline</v-icon></v-badge
              >
            </v-btn>
          </template>
          <v-list :items="items" item-props lines="three" max-width="350">
            <template v-slot:subtitle="{ subtitle }">
              <div v-html="subtitle"></div>
            </template>
          </v-list>
        </v-menu>
        <v-menu transition="slide-y-transition">
          <template v-slot:activator="{ props }">
            <v-btn v-bind="props">
              <v-avatar size="35">
                <v-img
                  cover
                  src="@/assets/myavatar.jpg"
                  alt="Safarmurod"
                  style="width: 100%; border-radius: 50%"
                />
              </v-avatar>
              <span>Safarmurod</span>
            </v-btn>
          </template>
          <v-list width="300">
            <v-list-item
              lines="two"
              prepend-avatar="@/assets/myavatar.jpg"
              title="Safarmurod O'rinov"
              subtitle="supermen0904@gmail.com"
            >
            </v-list-item>
            <v-list-item
              v-for="(menu, index) in menus"
              :key="index"
              :prepend-icon="menu.icon"
              :title="menu.title"
              :value="menu.title"
            >
            </v-list-item>
          </v-list>
        </v-menu>
      </v-app-bar>
      <v-container class="py-8 px-6" fluid>
        <router-view></router-view>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
// import HeaderVue from "./components/HeaderVue.vue";

const links = [
  ["mdi-view-dashboard", "Dashboard"],
  ["mdi-account", "Profile"],
  ["mdi-clipboard-list-outline", "Products"],
  ["mdi-clipboard-list-outline", "Order"],
  ["mdi-cog", "Settings"],
];
</script>

<script>
export default {
  data() {
    return {
      drawer: true,
      loaded: false,
      loading: false,
      menus: [
        { title: "Profile", icon: "mdi-account" },
        { title: "Passwords", icon: "mdi-key-outline" },
        { title: "Settings", icon: "mdi-cog" },
      ],
      items: [
        { type: "subheader", title: "Today" },
        {
          prependAvatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
          title: "Brunch this weekend?",
          subtitle: `<span class="text-primary">Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
        },
        { type: "divider", inset: true },
        {
          prependAvatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
          title: "Summer BBQ",
          subtitle: `<span class="text-primary">to Alex, Scott, Jennifer</span> &mdash; Wish I could come, but I'm out of town this weekend.`,
        },
        { type: "divider", inset: true },
        {
          prependAvatar: "https://cdn.vuetifyjs.com/images/lists/3.jpg",
          title: "Oui oui",
          subtitle:
            '<span class="text-primary">Sandra Adams</span> &mdash; Do you have Paris recommendations? Have you ever been?',
        },
        { type: "divider", inset: true },
        {
          prependAvatar: "https://cdn.vuetifyjs.com/images/lists/4.jpg",
          title: "Birthday gift",
          subtitle:
            '<span class="text-primary">Trevor Hansen</span> &mdash; Have any ideas about what we should get Heidi for her birthday?',
        },
        { type: "divider", inset: true },
        {
          prependAvatar: "https://cdn.vuetifyjs.com/images/lists/5.jpg",
          title: "Recipe to try",
          subtitle:
            '<span class="text-primary">Britta Holt</span> &mdash; We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
        },
      ],
    };
  },
  methods: {
    onClick() {
      this.loading = true;

      setTimeout(() => {
        this.loading = false;
        this.loaded = true;
      }, 2000);
    },
  },
};
</script>
