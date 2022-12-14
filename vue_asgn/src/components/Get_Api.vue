<template>
 
    <div >
      <button @click="GetApi">Fetch Data</button>
      <div v-for="items in post" :key="items">
        <h3>
          {{ items.id }}
          {{ items.title}}
          
        </h3>
      </div>
    </div>
  </template>
  <script>
  import axios from "axios";
  
  export default {
    name: "get_api",
    // components:{},
    data() {
      return {
        post: [],
      };
    },
    methods: {
      GetApi() {
        axios
          .get("https://dev.icc-health.com/dev/login")
          .then((response) => {
            console.log(response.data);
            this.post = response.data;
          });
      },
    },
  };
  </script>
  <style>

  </style>
  