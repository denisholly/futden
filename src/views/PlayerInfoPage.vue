<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <ion-grid>
        <ion-row v-if="currentPlayer">
            <ion-breadcrumbs>
                <ion-breadcrumb tab="players" href="/players">
                    Players
                </ion-breadcrumb>
                <ion-breadcrumb>
                    {{ currentPlayer.player.name }}
                </ion-breadcrumb>
            </ion-breadcrumbs>
        </ion-row>
        <ion-row v-if="currentPlayer">
            <div class="playerPhoto">
                <img :src="currentPlayer.player.photo">
            </div>
            <div class="playerNameClub">
                <h3> {{ currentPlayer.player.firstname }} {{ currentPlayer.player.lastname }} </h3>
                <p>{{ currentPlayer.statistics[0].games.position }}</p>
            </div>
        </ion-row>
        <ion-row v-if="currentPlayer">
            <div class="playerBasicInfo">
                <table>
                    <tr>
                        <th>Birth Date</th>
                        <th>Measurement</th>
                        <th>Country</th>
                    </tr>
                    <tr>
                        <td>{{ currentPlayer.player.birth.date }} ({{ currentPlayer.player.age }})</td>
                        <td>{{ currentPlayer.player.height }}, {{ currentPlayer.player.weight }}</td>
                        <td>{{ currentPlayer.player.nationality }}</td>
                    </tr>
                </table>
            </div>
        </ion-row>
        <ion-row v-if="currentPlayer">
            <div class="fullTitle">
                <h1 class="title">Statistics</h1>
            </div>
            <div class="playerStats" v-if="currentPlayer.statistics[0].games.position != 'Goalkeeper'">
                <div class="statsLeague">
                    <img :src="currentPlayer.statistics[0].team.logo">
                    <p>Chelsea - Premier League 2021/22</p>
                </div>
                <div class="statsText">
                    <p>Average Rating</p>
                    <p>Appearances</p>
                    <p>Starting 11</p>
                    <p>From bench</p>
                    <p>Minutes played</p>
                    <p>Subbed out</p>
                    <p>Goals</p>
                    <p>Shots</p>
                    <p>On target</p>
                    <p>Off target</p>
                    <p>Shot accuracy</p>
                    <p>Assists</p>
                    <p>Key passes</p>
                    <p>Accurate passes</p>
                    <p>Successful dribbles</p>
                    <p>Fouls drawn</p>
                    <p>Fouls commited</p>
                    <p>Yellow cards</p>
                    <p>Red cards</p>
                </div>
                <div class="statsValue">
                    <p :style="matchRatingClass">{{ Math.round(currentPlayer.statistics[0].games.rating * 100) / 100 }}</p>
                    <p>{{ currentPlayer.statistics[0].games.appearences }}</p>
                    <p>{{ currentPlayer.statistics[0].games.lineups }}</p>
                    <p>{{ currentPlayer.statistics[0].substitutes.in }}</p>
                    <p>{{ currentPlayer.statistics[0].games.minutes }}</p>
                    <p>{{ currentPlayer.statistics[0].substitutes.out }}</p>
                    <p>{{ currentPlayer.statistics[0].goals.total }}</p>
                    <p>{{ currentPlayer.statistics[0].shots.total }}</p>
                    <p>{{ currentPlayer.statistics[0].shots.on }}</p>
                    <p>{{ currentPlayer.statistics[0].shots.total - currentPlayer.statistics[0].shots.on }}</p>
                    <p>{{ Math.round(currentPlayer.statistics[0].shots.on / currentPlayer.statistics[0].shots.total * 100) }}%</p>
                    <p v-if="currentPlayer.statistics[0].goals.assists">{{ currentPlayer.statistics[0].goals.assists }}</p><p v-else>0</p>
                    <p>{{ currentPlayer.statistics[0].passes.key }}</p>
                    <p>{{ Math.round((100 - (currentPlayer.statistics[0].passes.total / currentPlayer.statistics[0].passes.accuracy)) * 100) / 100 }}%</p>
                    <p>{{ (Math.round((currentPlayer.statistics[0].dribbles.success / currentPlayer.statistics[0].dribbles.attempts) * 100) / 100) * 100 }}%</p>
                    <p>{{ currentPlayer.statistics[0].fouls.drawn }}</p>
                    <p>{{ currentPlayer.statistics[0].fouls.committed }}</p>
                    <p>{{ currentPlayer.statistics[0].cards.yellow }}</p>
                    <p>{{ currentPlayer.statistics[0].cards.red }}</p>
                </div>
            </div>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="js">
import { IonPage, IonContent, IonBreadcrumb, IonBreadcrumbs } from '@ionic/vue';
import axios from 'axios';

export default  {
    components: { IonContent, IonPage, IonBreadcrumb, IonBreadcrumbs},
    data() {
        return {
            currentPlayer: null,
        }
    },
    async created () {
        await this.fetchCurrentPlayer(this.$route.params.id);
    },
    methods: {
        async fetchCurrentPlayer(playerId) {
            try {
                const { data } = await axios.get('https://player-details-36818-default-rtdb.europe-west1.firebasedatabase.app/response.json');
                console.log(data);
                this.currentPlayer = data.find((el) => el.player.id == playerId);
                console.log(this.currentPlayer);
            } catch (error) {
                console.log(error);
            }
        }
    },
    computed: {
        matchRatingClass() {
            if (this.currentPlayer.statistics[0].games.rating >= 7) {
                return 'color: green';
            } else if (this.currentPlayer.statistics[0].games.rating >= 5.5) {
                return 'color: orange';
            } else {
                return 'color: red';
            }
        }
    }
}
</script>

<style scoped>
    h1 {
        padding: 0 20px;
    }

    ion-breadcrumbs {
        width: 100%;
        margin-bottom: 20px;
    }

    .playerPhoto {
        width: 100%;
        display: flex;
        justify-content: center;
    }

    .playerPhoto img {
        border-radius: 100%;
        width: 30%;
    }

    .playerNameClub {
        width: 80%;
        margin: auto;
        text-align: center;
    }

    .playerNameClub h3 {
        margin-bottom: 0;
    }

    .playerNameClub p {
        margin-top: 0;
        color: rgb(170, 170, 170);
    }

    .playerBasicInfo {
        background-color: #222325;
        width: 80%;
        margin: auto;
        padding: 10px;
        border-radius: 10px;
    }

    .playerBasicInfo table {
        width: 100%;
        text-align: center;
        font-size: 12px;
    }

    .playerBasicInfo th {
        font-weight: normal;
        color: rgb(170, 170, 170);
    }

    .fullTitle {
        width: 100%;
        border-bottom: 2px solid rgb(41, 41, 41);
        margin: 20px 0;
    }

    .playerStats {
        background-color: #222325;
        width: 90%;
        margin: auto;
        border-radius: 10px;
        padding: 0 10px;
        font-size: 12px;
    }

    .statsText {
        width: 50%;
        float: left;
    }

    .statsValue {
        width: 50%;
        float: right;
        text-align: right;
    }

    .statsLeague {
        width: 100%;
        display: flex;
        align-items: center;
    }

    .statsLeague img {
        width: 5%;
        float: left;
        margin-right: 5px;
    }

    .statsLeague p {
        width: 95%;
        float: right;
    }

</style>