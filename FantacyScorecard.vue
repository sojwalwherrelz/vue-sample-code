<template >
<div>
<h1>Fantacy Score Card Info</h1>
    <table border="1px">
        <tr>
            <td>Name</td>
            <td>Match Type</td>
            <td>venue</td>
            <td>date</td>
            <td>Date GMT</td>
            <td>status</td>
            <td>scores Info</td>
        </tr>
        <tr >
            <td>{{name}}</td>
            <td>{{matchType}}</td>
            <td>{{venue}}</td>
            <td>{{date}}</td>
            <td>{{dateTimeGMT}}</td>
            <td>{{status}}</td>
            <td>
                <ul v-for=" scores in score" v-bind:key="scores.id" >
                    <li>
                        r : {{ scores.r}}
                    </li>
                    <li>
                        W: {{ scores.w}}
                    </li>
                    <li>
                        O: {{ scores.o}}
                    </li>
                    <li>
                        inning : {{ scores.inning}}
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
    
        name:'FantacyScorecard',
        data(){
            return {
                list:undefined,
                teams:undefined,
                name:undefined,
                matchType:undefined,
                status:undefined,
                venue:undefined,
                date:undefined,
                dateTimeGMT:undefined,
                teamInfo:undefined,
                score:undefined,
            }
        },

        mounted(){
            const apikey = '%APIKEY%';
            axios.get(`https://api.cricapi.com/v1/match_scorecard?apikey=${apikey}&id=c50e6130-6718-4c11-b072-df382d24ed1c`)
            .then(res => {
                console.warn(res.data.data.name);
                this.matchType  = res.data.data.matchType;
                this.name  = res.data.data.name;
                this.status  = res.data.data.status;
                this.venue  = res.data.data.venue;
                this.date  = res.data.data.date;
                this.dateTimeGMT  = res.data.data.dateTimeGMT;
                this.teamInfo  = res.data.data.teamInfo;
                this.score  = res.data.data.score;
            }
            )
        }
    
}
</script>