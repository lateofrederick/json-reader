<template>
  <div id="wrapper">
    <main>
      <table class="table">
        <thead class="thead-dark"> 
          <tr>
            <th scope="col">Id</th>
            <th scope="col">Title</th>
            <th scope="col">Body</th>
          </tr>
        </thead>
    <tbody>
    <tr v-for="info in data" :key="info.id">
      <!--<th scope="row">1</th> -->
      <td>{{info.id}}</td>
      <td>{{info.title.charAt(0)}}</td>
      <td>{{info.body.charAt(0)}}</td>
    </tr> 
  </tbody>
      </table>
    </main>
  </div>
</template>

<script>
import SystemInformation from "./LandingPage/SystemInformation";
import axios from "axios";
import { log } from "util";

export default {
  name: "landing-page",
  components: { SystemInformation },
  data() {
    return {
      data: null
    };
  },
  methods: {
    open(link) {
      this.$electron.shell.openExternal(link);
    }
  },
  mounted() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then(response => (this.data = response.data));
    console.log(this.data);
  }
};
</script>

<style>
</style>
