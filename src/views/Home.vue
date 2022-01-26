<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to THE STATE" />
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  data: function () {
    return {
      info: {},
    };
  },
  created: function () {
    this.statesShow();
  },
  methods: {
    statesShow: function () {
      axios.get("/states").then((response) => {
        this.info = response.data;
        console.log(response.data);
      });
    },
  },
};
</script>
