<template >
<div>
<h1>Players List Data</h1>
    <table border='1px'>
        <tr>
            <td>Name</td>
            <td>Counrty Name</td>
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
    
        name:'PlayerSearch',
        data(){
            return {
                list:undefined
            }
        },

        mounted(){
            const apikey = '%APIKEY%';
            const Name = "Olive Smith"
            const playerName = Name.replace(" ", "%20");
            axios.get(`https://api.cricapi.com/v1/players?apikey=${apikey}&offset=0&search=${playerName}`)
            .then(res => {
                console.warn(res.data.data);
                this.list  = res.data.data;
            }
            )
        }
    
}
</script>