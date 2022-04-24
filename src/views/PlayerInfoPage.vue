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
            currentPlayer: null
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

</style>