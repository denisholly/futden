<template>
    <h1 class="title">Table</h1>

    <table>
        <tr>
            <th>#</th>
            <th>Team</th>
            <th>Pl</th>
            <th>W</th>
            <th>D</th>
            <th>L</th>
            <th>+/-</th>
            <th>Gd</th>
            <th>Pts</th>
        </tr>
        <tr v-for="team in teams" :key="team.id">
            <td> {{ team.position }} </td>
            <td> {{ team.name }} </td>
            <td> {{ team.pl }} </td>
            <td> {{ team.w }} </td>
            <td> {{ team.d }} </td>
            <td> {{ team.l }} </td>
            <td> {{ team.goals }} </td>
            <td> {{ team.gd }} </td>
            <td> {{ team.pts }} </td>
            
        </tr>
    </table>
</template>

<script>
    export default {
        inject: ['teams'],
        computed: {
            
        },
    }

</script>

<style scoped>
    table {
        width: 100%;
    }
</style>