<template>
<div class="col-6">
    <div class="row item">
        <div class="col-6">
            <img :src="datum.pic[0]" alt="">
        </div>
        <div class="col-6">        
            <p>{{datum.name}}</p>
            <p>{{datum.gender}}</p>
            <p>{{datum.priceRetail}}</p>
            <p>{{datum.priceRent}}</p>
            <ul>
                <li v-for="(value, index) in datum.size" :key="index">{{value}}</li>
            </ul>
            <p>{{datum.details}}</p>
            <ul>
                <li v-for="(value, index) in datum.tag" :key="index">{{value}}</li>
            </ul>
            <p>{{datum.status}}</p>
            <p>{{datum.date}}</p></div>
    </div>
</div>
</template>

<script>
export default {
    props:{
        datum: Object
    }
}
</script>

<style scoped>
    img{
        width: 100%;
    }
</style>