<template>
  <ion-page>
    <ion-header>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-grid>
        <ion-row>
            <div class="fullTitle">
                <h1 class="title">Manager</h1>
            </div>
            <table>
                <tr>
                    <th>#</th>
                    <th></th>
                    <th class="name">Name</th>
                    <th>Position</th>
                </tr>
                <tr class="teamInfo">
                    <td class="playerNumber">#</td>
                    <td>
                        <img src="https://pbs.twimg.com/media/E_LiBYrXoAIY6Qc?format=jpg&name=4096x4096" class="badge">
                    </td>
                    <td class="name">Thomas Tuchel</td>
                    <td class="position">MANAGER</td>
                </tr>
            </table>
        </ion-row>
        <ion-row>
          <div class="fullTitle">
            <h1 class="title">Players</h1>
          </div>
          <players-list></players-list>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonContent } from '@ionic/vue';
import PlayersList from '@/components/PlayersList.vue';

export default  {
  components: { IonHeader, IonContent, IonPage, PlayersList }
}
</script>

<style scoped>
  h1 {
    padding: 0 20px;
  }

  .fullTitle {
    width: 100%;
    border-bottom: 2px solid rgb(41, 41, 41);
    margin-bottom: 20px;
  }

  .managerSection {
      margin: auto;
      width: 95%;
      background-color: rgb(41, 41, 41);
      height: 200px;
  }

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