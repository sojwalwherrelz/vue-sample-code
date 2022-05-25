<template >
<div>
    <h1>MatchList Data</h1>
    <table border='1px'>
        <tr>
            <td>Name</td>
            <td>Match Type</td>
            <td>Status</td>
            <td>venue</td>
            <td>Date </td>
            <td>Teams</td>
        </tr>
        <tr v-for=" item in list " v-bind:key="item.id">
            <td>{{item.name}}</td>
            <td>{{item.matchType}}</td>
            <td>{{item.status}}</td>
            <td>{{item.venue}}</td>
            <td>{{item.date}}</td>
            <td>
                <ul>
                    <li v-for=" team in item.teams " v-bind:key="team.id">
                        {{team}}
                    </li>
                </ul>
            </td>
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
            axios.get(`https://api.cricapi.com/v1/matches?apikey=${apikey}&offset=0`)
            .then(res => {
                this.list  = res.data.data;
            }
            )
        }    
}
</script>
