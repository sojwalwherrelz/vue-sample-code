<template >
<div>
<h1>Countries Data</h1>
    <table border="1px">
        <tr>
            <td>Name</td>
            <td>flag</td>
        </tr>
        <tr v-for=" item in list " v-bind:key="item.id">
            <td>{{item.name}}</td>
            <td>{{item.genericFlag}}</td>
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
                console.warn(res.data.data);
                this.list  = res.data.data;
            }
            )
        }
    
}
</script>
