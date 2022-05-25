<template >
<div>
    <h1>Current Matches</h1>
    <table border='1px'>
        <tr>
            <td>Name</td>
            <td>Match Type</td>
            <td>Status</td>
            <td>venue</td>
            <td>date</td>
            <td>teams</td>
        </tr>
        <tr v-for="items in list" v-bind:key="items.id">
            <td>{{items.name}}</td>
            <td>{{items.matchType}}</td>              
            <td>{{items.status}}</td>              
            <td>{{items.venue}}</td>              
            <td>{{items.date}}</td>              
            <td>
                <ul v-for="teams in items.teams" v-bind:key="teams.id">
                    <li>
                        teams : {{teams}}
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
        name:'CurrentMatches',
        data(){
            return {
                list:undefined
            }
        },
        mounted(){
            const apikey = '%APIKEY%';
            axios.get(`https://api.cricapi.com/v1/currentMatches?apikey=${apikey}&offset=0`)
            .then(res => {
                this.list  = res.data.data;
            }
            )
        }
}
</script>
