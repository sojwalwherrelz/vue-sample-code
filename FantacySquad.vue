<template >
<div>
<h1>Fantacy Squad Info</h1>
    <table border="1px">
        <tr>
            <td>Name</td>
            <td>Team Info</td>
        </tr>
        <tr v-for=" item in list " v-bind:key="item.id">
            <td>{{item.teamName}}</td>
            <td>
                <ul v-for=" teamName in item.players" v-bind:key="teamName.id" >
                    <li>
                        name : {{ teamName.name}}
                    </li>
                    <li>
                        role: {{ teamName.role}}
                    </li>
                    <li>
                        battingStyle: {{ teamName.battingStyle}}
                    </li>
                    <li>
                        bowlingStyle : {{ teamName.bowlingStyle}}
                    </li>
                    <li>
                        Country : {{ teamName.country}}
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
    
        name:'FantacySquad',
        data(){
            return {
                list:undefined
            }
        },

        mounted(){
            const apikey = 'da2589ff-76cf-4b11-8654-080868ac896b';
            axios.get(`https://api.cricapi.com/v1/match_squad?apikey=${apikey}&id=c50e6130-6718-4c11-b072-df382d24ed1c`)
            .then(res => {
                console.warn(res.data.data);
                this.list  = res.data.data;
            }
            )
        }
    
}
</script>