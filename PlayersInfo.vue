<template >
<div>
    <h1>Players Info Data</h1>
    <table border='1px'>
        <tr>
            <td>Name</td>
            <td>Counrty Name</td>
            <td>Role</td>
            <td>Batting Style</td>
            <td>Place Of Birth</td>
            <td>Stats</td>
        </tr>
        <tr>
            <td>{{name}}</td>
            <td>{{country}}</td>              
            <td>{{role}}</td>              
            <td>{{battingStyle}}</td>              
            <td>{{placeOfBirth}}</td>              
            <td>
                <ul v-for="stat in stats" v-bind:key="stat.id">
                    <li>
                        fn : {{stat.fn}}
                    </li>
                    <li>
                        matchtype : {{stat.matchtype}}
                    </li>
                    <li>
                        stat :{{stat.stat}}
                    </li>
                    <li>
                        value : {{stat.value}}
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
        name:'PlayerInfo',
        data(){
            return {
                list:undefined,
                dateOfBirth:undefined,
                name:undefined,
                role:undefined,
                battingStyle:undefined,
                placeOfBirth:undefined,
                country:undefined,
                stats:undefined,
            }
        },
        mounted(){
            const apikey = '%APIKEY%';
            const id     = 'e9f47702-80c0-4a8f-91ff-61d391624ae6';
            axios.get(`https://api.cricapi.com/v1/players_info?apikey=${apikey}&id=${id}`)
            .then(res => {
                this.name           = res.data.data.name;
                this.dateOfBirth    = res.data.data.dateOfBirth;
                this.role           = res.data.data.role;
                this.battingStyle   = res.data.data.battingStyle;
                this.placeOfBirth   = res.data.data.placeOfBirth;
                this.country        = res.data.data.country;
                this.stats          = res.data.data.stats;
            }
            )
        }
}
</script>
