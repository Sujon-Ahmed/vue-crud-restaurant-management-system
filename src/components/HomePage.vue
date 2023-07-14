<template>
  <HeaderComponent />
  <h3 class="heading">Hello {{ name }}, Welcome to Home Page</h3>
  <br />
  <table
    style="
      width: 90%;
      margin: auto;
      align-items: center;
      justify-content: center;
    "
  >
    <tr>
      <th>#</th>
      <th>Name</th>
      <th>Contact</th>
      <th>Address</th>
      <th>Action</th>
    </tr>
    <tr v-for="restaurant in restaurants" :key="restaurant.id">
      <td>{{ restaurant.id }}</td>
      <td>{{ restaurant.name }}</td>
      <td>{{ restaurant.contact }}</td>
      <td>{{ restaurant.address }}</td>
      <td width="20%">
        <router-link :to="'/update-restaurant/' + restaurant.id"
          ><button class="btn update" type="button">Update</button></router-link
        >
        <button
          @click="deleteRestaurant(restaurant.id)"
          type="button"
          class="btn delete"
        >
          Delete
        </button>
      </td>
    </tr>
  </table>
</template>

<script>
import axios from "axios";
import HeaderComponent from "./HeaderComponent.vue";
export default {
  name: "HomePage",
  data() {
    return {
      name: "",
      restaurants: [],
    };
  },
  components: {
    HeaderComponent,
  },
  methods: {
    async deleteRestaurant(id) {
      let result = await axios.delete("http://localhost:3000/restaurants/" + id);
      if (result.status == 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem("user-info");
      this.name = JSON.parse(user).name;
      if (!user) {
        this.$router.push({ name: "SignUp" });
      }
      let result = await axios.get("http://localhost:3000/restaurants");
      this.restaurants = result.data;
    },
  },
  async mounted() {
    this.loadData();
  },
};
</script>

<style>
.heading {
  margin-top: 10px;
}
table,
th,
td {
  border: 1px solid black;
}
.btn.update {
  background: green;
  color: #fff;
  cursor: pointer;
}
.btn.delete {
  background: red;
  color: #fff;
  cursor: pointer;
}
</style>
