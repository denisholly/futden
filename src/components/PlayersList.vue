<template>
        <table>
            <tr>
                <th>#</th>
                <th></th>
                <th class="name">Name</th>
                <th>Position</th>
            </tr>
            <tr v-for="player in players" :key="player.id" class="teamInfo">
                <td class="playerNumber"> {{ player.number }} </td>
                <td>
                    <img :src="player.photo" class="badge">
                </td>
                <td class="name"> {{ player.name }} </td>
                <td class="position"> {{ player.short_position }} </td>
            </tr>
        </table>
</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                players: [],
            }
        },
        created () {
            axios.get('https://futden-chelsea-players-default-rtdb.europe-west1.firebasedatabase.app/response.json')
                .then(res => {
                    const players = res.data[0].players;
                    console.log('Players', players);

                    for (let key in players) {
                        const player = players[key];
                        this.players.push(player);
                    }
                })
                .catch(error => console.log(error))
        },
    }

</script>

<style scoped>

    table {
        width: 95%;
        margin: auto;
        font-size: 13px;
        border-collapse: separate;
        border-spacing: 0 1em;
    }

    .badge {
        border-radius: 50%;
        width: 30px;
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

    .position {
        text-align: center;
        color: #696969;
    }

    .name {
        text-align: start;
    }

    .playerNumber {
        text-align: center;
        color: dodgerblue;
    }

    th {
        padding: 0 20px;
    }

</style>