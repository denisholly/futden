<template>
    <div class="tableIonic">
        <ion-row class="tableHeader">
            <ion-col>#</ion-col>
            <ion-col colspan="2">TEAM</ion-col>
            <ion-col>Pl</ion-col>
            <ion-col>W</ion-col>
            <ion-col>D</ion-col>
            <ion-col>L</ion-col>
            <ion-col>+/-</ion-col>
            <ion-col>Gd</ion-col>
            <ion-col>Pts</ion-col>
        </ion-row>
        <ion-row class="tableContent" v-for="team in top5Teams" :key="team.rank">
            <ion-col> {{ team.rank }} </ion-col>
            <ion-col>
                    <img :src="team.team.logo" class="badge">
            </ion-col>
            <ion-col> {{ team.team.shortName }} </ion-col>
            <ion-col> {{ team.all.played }} </ion-col>
            <ion-col> {{ team.all.win }} </ion-col>
            <ion-col> {{ team.all.draw }} </ion-col>
            <ion-col> {{ team.all.lose }} </ion-col>
            <ion-col> {{ team.all.goals.for }}/{{ team.all.goals.against }} </ion-col>
            <ion-col> {{ team.goalsDiff }} </ion-col>
            <ion-col> {{ team.points }} </ion-col>
        </ion-row>
    </div>
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
    .tableIonic {
        width: 80%;
        margin: auto;
        font-size: 13px;
    }

    .tableHeader {
        float: left;
        width: 100%;
        border-radius: 5px;
        font-size: 11px;
    }

    .tableContent {
        padding: 15px 5px;
        margin-top: 15px;
        background-color: #222325;
        border-radius: 10px;
    }

    ion-col {
        display: flex;
        align-items: center;
        height: 40px;
    }

    .badge {
        width: 20px;
    }
</style>