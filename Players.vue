<template >
<div>
<h1>Players List Data</h1>
    <table border="1px">
        <tr>
            <td>Name</td>
            <td>Country Name</td>
        </tr>
        <tr v-for=" item in list " v-bind:key="item.id">
            <td>{{item.name}}</td>
            <td>{{item.country}}</td>        
        </tr>
    </table>
</div>
</template>
<script>

import axios from "axios"

export default {
      apikey:'%APIKEY%',
        name:'PlayersApi',
        data(){
            return {
                list:undefined
            }
        },

        mounted(){
            axios.get(`https://api.cricapi.com/v1/players?apikey={apikey}&offset=0`)
            .then(res => {
                this.list  = res.data.data;
            }
            )
        }
    
}
</script>
