<template>
  <div class="hello">
    <tr v-bind="user">
      <td>Id :</td>
      <td>{{ user.id }}</td>
    </tr>
    <tr>
      <td>Name :</td>
      <td>{{ user.name }}</td>
    </tr>
    <tr>
      <td>UserName :</td>
      <td>{{ user.username }}</td>
    </tr>
    <tr>
      <td>Email :</td>
      <td>{{ user.email }}</td>
    </tr>
    <tr>
      <td>Address-Street :</td>
      <td>{{ user.address.street }}</td>
    </tr>
    <tr>
      <td>Address-Suite:</td>
      <td>{{ user.address.suite }}</td>
    </tr>
    <tr>
      <td>Address-City :</td>
      <td>{{ user.address.city }}</td>
    </tr>
    <tr>
      <td>Address-Zipcode :</td>
      <td>{{ user.address.zipcode }}</td>
    </tr>
    <tr>
      <td>Address-Geo-Lat :</td>
      <td>{{ user.address.geo.lat }}</td>
    </tr>
    <tr>
      <td>Address-Geo-Lng :</td>
      <td>{{ user.address.geo.lng }}</td>
    </tr>

    <tr>
      <td>Phone :</td>
      <td>{{ user.phone }}</td>
    </tr>
    <tr>
      <td>Website :</td>
      <td>{{ user.website }}</td>
    </tr>

    <tr>
      <td>Comapany-Name:</td>
      <td>{{ user.company.name }}</td>
    </tr>

    <tr>
      <td>Comapany-CatchParse :</td>
      <td>{{ user.company.catchPhrase }}</td>
    </tr>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, axios);
export default {
  name: "HelloWorld",
  data() {
    return {
      user: null,
    };
  },
  mounted() {
    Vue.axios
      .get(
        "https://jsonplaceholder.typicode.com/users/" + this.$route.params.id
      )
      .then((resp) => {
        this.user = resp.data;
        console.log(resp.data);
      });
  },
};
</script>