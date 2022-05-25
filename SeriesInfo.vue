<template >
<div>
<h1>Series Info </h1>
    <table border='1px'>
        <tr>
            <td>Name</td>
            <td>Start Date</td>
            <td>End Date</td>
            <td>ODI</td>
            <td>T20</td>
            <td>Test</td>
            <td>Squads</td>
            <td>Matches</td>
        </tr>
        <tr>
            <td>{{name}}</td>
            <td>{{startdate}}</td>              
            <td>{{enddate}}</td>              
            <td>{{odi}}</td>              
            <td>{{t20}}</td>              
            <td>{{test}}</td>              
            <td>{{squads}}</td>              
            <td>{{matches}}</td>              
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
                startdate:undefined,
                enddate:undefined,
                name:undefined,
                odi:undefined,
                t20:undefined,
                test:undefined,
                squads:undefined,
                matches:undefined,
            }
        },

        mounted(){
        const apikey = '%APIKEY%';
            axios.get(`https://api.cricapi.com/v1/series_info?apikey=${apikey}&id=48f379be-f178-473f-8788-373696c2ec2c`)
            .then(res => {
                this.name  = res.data.data.info.name;
                this.startdate  = res.data.data.info.startdate;
                this.enddate  = res.data.data.info.enddate;
                this.odi  = res.data.data.info.odi;
                this.t20  = res.data.data.info.t20;
                this.test  = res.data.data.info.test;
                this.squads  = res.data.data.info.squads;
                this.matches  = res.data.data.info.matches;
            }
            )
        }
    
}
</script>
