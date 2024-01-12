<template>
  <div class="dashboard">
    <v-subheader class="d-flex justify-space-between align-center">
      <h3>Dashboard</h3>
      <v-btn color="success">View Orders</v-btn>
    </v-subheader>
    <v-row>
      <v-col lg="7" cols="12"
        ><v-alert text="" variant="outlined" type="success" class="my-5">
          <strong>Login Successfully</strong></v-alert
        >
        <v-row>
          <v-col
            lg="6"
            cols="12"
            v-for="(item, index) in activities"
            :key="index"
          >
            <v-card elevation="2" class="rounded-lg">
              <v-card-text class="d-flex justify-space-between align-center">
                <div class="">
                  <strong>{{ item.title }}</strong
                  ><br />
                  <small>Last 2 weeks</small>
                </div>
                <v-avatar :color="item.color" size="60">
                  <span class="white--text">{{ item.amount }}</span>
                </v-avatar>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
      <v-col lg="5" cols="12" class="my-5">
        <v-card title="Activities" class="rounded-lg" elevation="2">
          <v-timeline
            side="end"
            align="start"
            style="border-top: 1px solid lightgray"
          >
            <v-timeline-item dot-color="pink" size="small">
              <div class="d-flex">
                <strong class="me-4">5pm</strong>
                <div>
                  <strong>New Icon</strong>
                  <div class="text-caption">Mobile App</div>
                </div>
              </div>
            </v-timeline-item>

            <v-timeline-item dot-color="teal-lighten-3" size="small">
              <div class="d-flex">
                <strong class="me-4">3-4pm</strong>
                <div>
                  <strong>Design Stand Up</strong>
                  <div class="text-caption mb-2">Hangouts</div>
                </div>
              </div>
            </v-timeline-item>

            <v-timeline-item dot-color="pink" size="small">
              <div class="d-flex">
                <strong class="me-4">12pm</strong>
                <div>
                  <strong>Lunch break</strong>
                  <div class="text-caption">Mobile App</div>
                </div>
              </div>
            </v-timeline-item>
          </v-timeline></v-card
        >
      </v-col>
    </v-row>
    <v-row>
    <v-col cols="12"> 
       <v-table style="border: 1px solid lightgray;border-radius: 10px;" class="px-3 py-3">
        <caption style="font-size: 25px;">Recent Orders</caption>
        <thead>
          <tr>
            <th class="text-left">Name</th>
            <th class="text-left">Calories</th>
            <th class="text-left">Price</th>
            <th class="text-left">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in desserts" :key="item.name">
            <td>{{ item.name }}</td>
            <td>{{ item.calories }}</td>
            <td>{{ item.price }}</td>
            <td><v-btn variant="outlined" color="green">View</v-btn></td>
          </tr>
        </tbody>
      </v-table>
      <v-row justify="center">
        <v-col cols="12">
            <v-pagination
              v-model="page"
              density="compact"
              class="my-2"
              :length="7"
            ></v-pagination>
        </v-col>
      </v-row>
    </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  data() {
    return {
      activities: [
        { title: "Total Products", color: "red", amount: 4545 },
        { title: "Total Categories", color: "green", amount: 25 },
        { title: "Total Orders", color: "blue", amount: 125 },
        { title: "Pending Orders", color: "orange", amount: 1245 },
      ],
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
          price:1200
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
          price:1200
        },
        {
          name: "Eclair",
          calories: 262,
          price:1200
        },
        {
          name: "Cupcake",
          calories: 305,
          price:1200
        },
        {
          name: "Gingerbread",
          calories: 356,
          price:1200
        },
      ],
      page:1
    };
  },
};
</script>
<style></style>
