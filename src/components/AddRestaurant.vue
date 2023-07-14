<template>
  <HeaderComponent />
  <form class="restaurantForm">
    <h3>Add Restaurant</h3>
    <hr />
    <input
      type="text"
      name="name"
      id="name"
      v-model="restaurant.name"
      autocomplete="off"
      placeholder="Enter Name"
    />
    <input
      type="text"
      name="address"
      id="address"
      v-model="restaurant.address"
      autocomplete="off"
      placeholder="Enter Address"
    />
    <input
      type="text"
      name="contact"
      id="contact"
      v-model="restaurant.contact"
      autocomplete="off"
      placeholder="Enter Contact"
    />
    <button @click="addRestaurant" id="submitBtn" type="button">
      Add Restaurant
    </button>
  </form>
</template>

<script>
import axios from "axios";
import HeaderComponent from "./HeaderComponent.vue";
export default {
  name: "AddRestaurant",
  data() {
    return {
      restaurant: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  components: {
    HeaderComponent,
  },
  methods: {
    async addRestaurant() {
      if (
        this.restaurant.name != "" &&
        this.restaurant.address != "" &&
        this.restaurant.contact != ""
      ) {
        const result = await axios.post("http://localhost:3000/restaurants", {
          name: this.restaurant.name,
          address: this.restaurant.address,
          contact: this.restaurant.contact,
        });
        console.warn(result);
      } else {
        alert("Something Went Wrong!");
      }
    },
  },
};
</script>

<style scoped>
h3 {
  margin-bottom: 10px;
}
hr {
  margin-bottom: 20px;
}
.restaurantForm {
  margin: auto;
  width: 450px;
  height: 350px;
  padding: 20px 5px;
  margin-top: 50px;
  background: #fff;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
  border-radius: 4px;
}

.restaurantForm input {
  display: block;
  padding: 10px;
  width: 90%;
  margin: auto;
  margin-bottom: 20px;
  border: 1px solid skyblue;
  outline: none;
  border-radius: 4px;
}
#submitBtn {
  width: 90%;
  height: 35px;
  margin-top: 20px;
  border: none;
  background: linear-gradient(to right, #7f7fd5, #86a8e7, #91eae4);
  cursor: pointer;
  border-radius: 2px;
  font-size: 16px;
  text-transform: uppercase;
  color: #fff;
}
</style>
