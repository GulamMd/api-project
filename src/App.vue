<template>
  <h1>User Data</h1>
  <ul class="item" v-for="list in lists" :key="list">
    <li>{{list.id}}</li>
    <li>{{list.email}}</li>
    <li>{{list.first_name}}</li>
    <li><img :src="list.avatar"/></li>
  </ul>
</template>

<script>

import axios from 'axios'
export default {
  
  name: 'App',
  data() {
    return {
      lists: []
    }
  },
  async mounted() {
    let result = await axios.get("https://reqres.in/api/users?page=1");
    console.warn("Api result",result.data.data);
    this.lists=result.data.data;
  }
  
}
</script>

<style>
  .item {
    display: flex;
    text-align: center;
  }
  .item li {
    display: inline-block;
    width: 200px;
    border: 1px black solid;
    text-align: center;
    padding: 23px;
  }
  .item li img {
    width:120px;
  }
</style>
