<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>WELCOME TO THE STATE</h1>
    <br />
    <p></p>
    <br />
    <h2>State ABV:</h2>
    <input type="text" v-model="input" />
    <button v-on:click="showState()">Search</button>
    <br />
    <p></p>
    <p></p>
    <h2>{{ show[0] }}</h2>
    <h3>Median Household Income: ${{ show[1] }}</h3>
    <h3>Percentage of Seasonally Unemployed: {{ show[2] }}%</h3>
    <h3>Percentage of Metropolitan Population: {{ show[3] }}%</h3>
    <h3>Percentage with High School Diploma: {{ show[4] }}%</h3>
    <br />
    <p></p>
    <div v-for="state in states" v-bind:key="state.id">
      <h2>{{ state[0] }}</h2>
      <h3>Median Household Income: ${{ state[1] }}</h3>
      <h3>Percentage of Seasonally Unemployed: {{ state[2] }}%</h3>
      <h3>Percentage of Metropolitan Population: {{ state[3] }}%</h3>
      <h3>Percentage with High School Diploma: {{ state[4] }}%</h3>
      <br />
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
      input: "",
      show: [],
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
    showState: function () {
      axios.get("/states/" + this.input).then((response) => {
        this.show = response.data;
        console.log(response.data);
      });
    },
  },
};
</script>
