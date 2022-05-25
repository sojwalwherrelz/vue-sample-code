<template >
<div>
<h1>Match Info </h1>
    <table border='1px'>
        <tr>
            <td>Name</td>
            <td> Date</td>
            <td>Date time GMT</td>
            <td>match type</td>
            <td>Status</td>
            <td>Venue</td>
           
        </tr>
        <tr >
            <td>{{name}}</td>
            <td>{{date}}</td>
            <td>{{dateTimeGMT}}</td>
            <td>{{matchType}}</td>
            <td>{{status}}</td>
            <td>{{venue}}</td>
        </tr>
    </table>
</div>
</template>
<script>

import axios from "axios"

export default {
        
        name:'SeriesInfo',
        data(){
            return {
                date:undefined,
                dateTimeGMT:undefined,
                name:undefined,
                matchType:undefined,
                venue:undefined,
                statsu:undefined,
            }
        },

        mounted(){
            const apikey = '%APIKEY%';
            axios.get(`https://api.cricapi.com/v1/match_info?apikey=${apikey}&id=7d4496c7-f353-4ad9-b20f-a6314e181acf`)
            .then(res => {
                console.log(res.data.data.name)
                this.name  = res.data.data.name;
                this.date  = res.data.data.date;
                this.dateTimeGMT  = res.data.data.dateTimeGMT;
                this.matchType  = res.data.data.matchType;
                this.venue  = res.data.data.venue;
                this.status  = res.data.data.status;
               
                
            }
            )
        }
    
}
</script>