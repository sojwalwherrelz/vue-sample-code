<template >
<div>
    <h1>Fantacy Points Info</h1>
    <table border="1px">
        <tr>
            <td>Name</td>
            <td>Batting Info</td>
            <td>Bowling Info</td>
            <td>Catchinging Info</td>
        </tr>
        <tr v-for=" innings in list " v-bind:key="innings.id">
            <td>{{innings.inning}}</td>
            <td>
                <ul v-for=" batting in innings.batting" v-bind:key="batting.id" >
                    <li>
                        name : {{ batting.name}}
                    </li>
                    <li>
                        role: {{ batting.points}}
                    </li>
                </ul>
            </td>
            <td>
                <ul v-for=" bowling in innings.bowling" v-bind:key="bowling.id" >
                    <li>
                        name : {{ bowling.name}}
                    </li>
                    <li>
                        role: {{ bowling.points}}
                    </li>
                </ul>
            </td>
            <td>
                <ul v-for=" catching in innings.catching" v-bind:key="catching.id" >
                    <li>
                        name : {{ catching.name}}
                    </li>
                    <li>
                        role: {{ catching.points}}
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
        name:'FantacyPoints',
        data(){
            return {
                list:undefined
            }
        },
        mounted(){
            const apikey = '%APIKEY%';
            axios.get(`https://api.cricapi.com/v1/match_points?apikey=${apikey}&id=c50e6130-6718-4c11-b072-df382d24ed1c`)
            .then(res => {
                this.list  = res.data.data.innings;
            }
            )
        }
}
</script>
