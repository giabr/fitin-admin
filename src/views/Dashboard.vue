<template>
    <div id="dashboard" class="container">
        <div class="row">
            <div class="col-2">
                <form-input></form-input>   
            </div>
            <div class="col-10">
                <katalog></katalog>
            </div>
        </div>
    </div>
</template>

<script>
import FormInput from '../components/Input'
import Katalog from '../components/Output'

export default {
components:{
    FormInput,
    Katalog
},
data: function(){
    return{
        data: null
    }
}
}
</script>

<style>
    #dashboard{
        padding: 60px 0;
    }
    .primColor{
        color: #5ac8d8;
    }
    .form-input{
        padding: 10px 0;
    }
</style>