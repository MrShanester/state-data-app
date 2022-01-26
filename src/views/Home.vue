<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>WELCOME TO THE STATE</h1>
    <div v-for="state in states" v-bind:key="state.id">
      <h2>{{ state[0] }}</h2>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  data: function () {
    return {
      states: {},
    };
  },
  created: function () {
    this.statesShow();
  },
  methods: {
    statesShow: function () {
      axios.get("/states").then((response) => {
        this.states = response.data;
        console.log(response.data);
      });
    },
  },
};
</script>
