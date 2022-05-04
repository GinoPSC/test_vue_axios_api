<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
  <h1>{{titulo}}</h1>
  <div class='api_table_post'>
    <table>
      <h3>Test de estado</h3>
      <p>{{postStatus}}</p>
    </table>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'HomeView',
  data(){
    return{
      titulo: 'Test api consumption with axios',
      postStatus: null
    }
  },
  created(){
    let url = 'https://jsonplaceholder.typicode.com/posts';
    let posteada = {
      title: "hola",
      body: "mundo"
    };

    axios.post(url,posteada)
    .then(response => {
      this.postStatus = response
    });
  }
}

</script>

<style>
  .api_table_post table{
    margin: auto;
  }
</style>