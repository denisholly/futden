<template>
    <table>
        <tr>
            <th></th>
            <th>#</th>
            <th colspan="2">TEAM</th>
            <th>Pl</th>
            <th>W</th>
            <th>D</th>
            <th>L</th>
            <th>+/-</th>
            <th>Gd</th>
            <th>Pts</th>
        </tr>
        <tr v-for="team in top5Teams" :key="team.rank">
            <td></td>
            <td> {{ team.rank }} </td>
            <td>
                    <img :src="team.team.logo" class="badge">
            </td>
            <td> {{ team.team.shortName }} </td>
            <td> {{ team.all.played }} </td>
            <td> {{ team.all.win }} </td>
            <td> {{ team.all.draw }} </td>
            <td> {{ team.all.lose }} </td>
            <td> {{ team.all.goals.for }}/{{ team.all.goals.against }} </td>
            <td> {{ team.goalsDiff }} </td>
            <td> {{ team.points }} </td>
        </tr>
    </table>
</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                teams: [],
            }
        },
        created () {
            axios.get('https://vue-http-demo-8d3ce-default-rtdb.europe-west1.firebasedatabase.app/response.json')
                .then(res => {
                    const standings = res.data[0].league.standings[0];
                    console.log('Standings', standings);

                    for (let key in standings) {
                        const team = standings[key];
                        this.teams.push(team);
                    }
                    
                    console.log('Teams', this.teams);
                })
                .catch(error => console.log(error))
        },
        computed: {
            top5Teams () {
                return this.teams.slice(0, 20);
            }
        }
        
    }

</script>

<style scoped>
    table {
        width: 100%;
        width: 95%;
        margin: auto;
        font-size: 13px;
        text-align: left;
        background-color: #222325;
        border-radius: 15px;
    }

    th {
        color: rgb(165, 165, 165);
        height: 40px;  
    }

    td {
        height: 40px;
        border-bottom: 1px solid black;
        border-top: 1px solid black;
    }

    .badge {
        width: 20px;
    }
</style>