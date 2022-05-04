<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
  <h1>{{titulo}}</h1>
  <div class='api_table_get'>
    <table>
      <tbody>
        <tr v-for="things in tasks" :key="things.id">
          <td> {{things.id}} </td>
          <td> {{things.title}} </td>
          <td> {{things.completed}} </td>
          <td> {{things.userid}} </td>
        </tr>
      </tbody>
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
      tasks: null
    }
  },
  mounted(){
    this.getTasks();
  },
  methods:{
    getTasks(){
      axios.get('https://jsonplaceholder.typicode.com/todos')
      .then(response => {
        this.tasks = response.data
      }).catch(e=> console.log(e))
    }
  }
}
</script>

<style>
  .api_table_get table{
    margin: auto;
  }
</style>