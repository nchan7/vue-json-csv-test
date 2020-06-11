<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h2>This is an app that tests the json to csv converter</h2>
    <h4>The app uses the two npm modules: jsonexport and file-saver</h4>
    <br />
    <button v-on:click="exportData">
      Download Test Data
    </button>
  </div>
</template>

<script>
import consultingData from "./data/ConsultingStudioFromHome.json";
const jsonexport = require("jsonexport");
import { saveAs } from "file-saver";

export default {
  name: "App",
  methods: {
    exportData() {
      jsonexport(consultingData, (err, csv) => {
        if (err) {
          return console.log(err);
        }
        let blob = new Blob([csv]);
        saveAs(blob, "ConsultingStudioFromHome.csv");
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
