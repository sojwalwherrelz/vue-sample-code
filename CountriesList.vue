<template>
<div>
<h1>Countries List</h1>
    <table border="1px">
        <tr>
            <td>Name</td>
            <td>flag</td>
        </tr>
        <tr v-for=" item in list " v-bind:key="item.id">
            <td>{{item.name}}</td>
            <td><img :src="item.genericFlag" class="flgimg"></td>
        </tr>
    </table>
</div>
</template>
<script>
import axios from "axios"
export default {
        name:'CountriesApi',
        data(){
            return {
                list:undefined
            }
        },
        mounted(){
            const apikey = '%APIKEY%';
            axios.get(`https://api.cricapi.com/v1/countries?apikey=${apikey}&offset=0`)
            .then(res => {
                this.list  = res.data.data;
            }
            )
        }
}
</script>
<style scoped>
.flgimg{
    width: 100px;
    height: 100px;
}
</style>
