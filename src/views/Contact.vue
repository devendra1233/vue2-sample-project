<template>
  <div class="container">
    <h3>Users:</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Name</th>
          <th scope="col">Email</th>
          <th scope="col">City</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, id) in users" :key="id">
          <th scope="row">{{ user.id }}</th>
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.address.city }}</td>
        </tr>
      </tbody>
    </table>
<br><br><br><br>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Name</th>
          <th scope="col">Email</th>
          <th scope="col">City</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, id) in users1" :key="id">
          <th scope="row">{{ user.id }}</th>
          <td>{{ user.name }}</td>
          <td>{{ user.created_at }}</td>
          <td>{{ user.published_at }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Users",
  data() {
    return {
      users: null,
      users1: null,
    };
  },
  created: function () {
    axios.get("https://jsonplaceholder.typicode.com/users").then((res) => {
      this.users = res.data;
    });

    axios
      .get(
        "https://api.storyblok.com/v1/cdn/stories/home?version=draft&token=slyAvbv9cR57Wj0MZfQnoAtt&cv=1638944076"
      )
      .then((res) => {
        this.users1 = res.data;
        console.log("this.users1", this.users1);
      });
  },
};
</script>

<style>
table, th, td {
  border: 1px solid black;
}
</style>