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
            <tr v-for="team in top5Teams" :key="team.rank" class="teamInfo" :class="top4Style(team.rank)">
                <td :class="top4Style(team.rank)"></td>
                <td> {{ team.rank }} </td>
                <td>
                    <img :src="team.team.logo" class="badge">
                </td>
                <td> {{ team.team.name }} </td>
                <td class="teamStats"> {{ team.all.played }} </td>
                <td class="teamStats"> {{ team.all.win }} </td>
                <td class="teamStats"> {{ team.all.draw }} </td>
                <td class="teamStats"> {{ team.all.lose }} </td>
                <td class="teamStats"> {{ team.all.goals.for }}/{{ team.all.goals.against }} </td>
                <td class="teamStats"> {{ team.goalsDiff }} </td>
                <td class="teamStats"> {{ team.points }} </td>
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
        },
        methods: {
            top4Style(id) {
                if (id < 5) {
                    return 'clStyle';
                } else if (id === 5) {
                    return 'elStyle';
                } else if (id > 17) {
                    return 'relStyle';
                }
            }
        }
        
    }

</script>

<style scoped>

    table {
        width: 95%;
        margin: auto;
        font-size: 13px;
        border-collapse: separate;
        border-spacing: 0 2em;
    }

    .badge {
        width: 20px;
    }

    td:first-child {
        padding: 0 5px;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }

    td:last-child {
        padding: 0 5px;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
    }

    td {
        padding: 15px 0;
    }

    .teamInfo {
        background-color: #222325;
    }

    .teamStats {
        text-align: center;
        padding: 0 3px;
    }

    .clStyle {
        border-left: 2px solid green;
    }

    .elStyle {
        border-left: 2px solid orange;
    }

    .relStyle {
        border-left: 2px solid red;
    }

</style>