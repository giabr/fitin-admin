<template>
  <div id="inputBar">
    <h4 class="title">Input Data</h4>
    <br>
    <form @submit="add">
            <input class="input" v-model="object.name" placeholder="product name">
            <br>
            <input class="input" v-model="object.priceRent" placeholder="price rent">
            <br>
            <input class="input" v-model="object.priceRetail" placeholder="price retail">
            <br>
            <input class="input" v-model="object.pic[0]" placeholder="pic link 1">
            <br>
            <input class="input" v-model="object.pic[1]" placeholder="pic link 2">
            <br>
            <input class="input" v-model="object.pic[2]" placeholder="pic link 3">
            <br>
                <input type="checkbox" id="M" value="M" v-model="object.size">
                <label for="M">M</label>
                <input type="checkbox" id="L" value="L" v-model="object.size">
                <label for="L">L</label>
                <input type="checkbox" id="XL" value="XL" v-model="object.size">
                <label for="XL">XL</label>
            <br>
            <textarea class="input" v-model="object.details" placeholder="details"></textarea>
            <select class="input" v-model="object.gender">
                <option disabled value="">Please select one</option>
                <option value="true">Male</option>
                <option value="false">Female</option>
            </select>
            <br>
                <input type="checkbox" id="wedding" value="Wedding" v-model="object.tag">
                <label for="wedding">Wedding</label>
                <input type="checkbox" id="grad" value="Graduation" v-model="object.tag">
                <label for="grad">Graduation</label>
            <br>
            <button class="btn button" type="submit" value="Submit">Add</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    data:function(){
        return{
            object:{
                name: null,
                gender: null,
                priceRetail: null,
                priceRent: null,
                pic: [],
                tag: [],
                status: 0,
                details: null,
                date: new Date(),
            }, 
        }
    },
    methods:{
        add(){
            axios.post(`http://localhost:3000/item`, this.object)
            .then(response => {
            // this.data = response.data;
                alert('Sukses', response);
            }).catch(e => {
            this.errors.push(e);
            });
        }
    }
}
</script>

<style>
    .button{
        float: right;
        background-color: #5ac8d8 !important;
        color: white !important;
    }
    .button:hover{
        background-color: white !important;
        color: black !important;
    }
    #inputBar{
        height: 100%;
        width: 300px;
        position: fixed;
        z-index: 1;
        top: 0;
        left: 0;
        background-color: #f1f8ff;
    }
    .title{
        margin: 20px;
    }
    form{
        margin-left: 20px;
        margin-right: 20px;
    }
    textarea{
        height: 200px;
        width: 100%;
    }
    .input{
        margin-bottom: 5px;
        width: 100%;
    }
</style>