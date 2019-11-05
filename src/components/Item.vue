<template>
<div class="col-6">
    <div class="row item">
        <div class="col-6">
            <img :src="datum.pic[0]" alt="">
        </div>
        <div class="col-6">
            <p>ID : {{datum._id}}</p>        
            <p>Name : {{datum.name}}</p>
            <p v-if="datum.gender === true">Gender : Male</p>
            <p v-else>Gender : Female</p>
            <p>Retail : {{rupiah(datum.priceRetail)}}</p>
            <p>Rent : {{rupiah(datum.priceRent)}}</p>
            <p>Size :</p>
            <ul>
                <li v-for="(value, index) in datum.size" :key="index">{{value}}</li>
            </ul>
            <p>Details : {{datum.details}}</p>
            <p>Tag :</p>
            <ul>
                <li v-for="(value, index) in datum.tag" :key="index">{{value}}</li>
            </ul>
            <p>Status : {{datum.status}}</p>
            <p>Date : {{datum.date}}</p>
        </div>
    </div>
    <button v-on:click="deleteItem(datum._id)">Delete</button>
</div>
</template>

<script>
import axios from 'axios'
const convertRupiah = require('rupiah-format')

export default {
    props:{
        datum: Object
    },
    methods:{
        deleteItem(id){
            axios.delete(`http://localhost:3000/item/` + id)
            .then(response => {
            // this.data = response.data;
                alert('Delete', response);
                document.location.reload(true);
            }).catch(e => {
            this.errors.push(e);
            });
        },
        rupiah(price){
            return convertRupiah.convert(price)
        }
    }
}
</script>

<style scoped>
    img{
        width: 100%;
    }
</style>