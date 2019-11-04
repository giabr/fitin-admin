<template>
  <div class="row">
      <item v-for="(data, index) in data" :key="index" :datum="data"></item>
  </div>
</template>

<script>
import axios from 'axios'
import Item from './Item'

export default {
components:{
    Item
},
data: function(){
    return{
        data: null
    }
},
created() {
  axios.get(`https://fitin-server.herokuapp.com/item`)
    .then(response => {
      this.data = response.data;
      // console.log(response.data);
    }).catch(e => {
      this.errors.push(e);
    });
}
}
</script>

<style>

</style>