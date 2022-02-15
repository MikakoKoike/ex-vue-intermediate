<template>
  <div class="team">
    <h1>野球チーム一覧</h1>
    <table>
      <tr v-for="team of teamsInfo" v-bind:key="team.id">
        <router-link :to="'/teamDetail/' + team.id">
          <td>
            {{ team.teamName }}
          </td>
        </router-link>
      </tr>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Team } from "@/types/team";
@Component
export default class Ex01 extends Vue {
  //gettersのgetTeamsを取得して返す
  get teamsInfo(): string {
    return this.$store.getters.getTeams;
  }
}
</script>

<style scoped>
.team {
  text-align: left;
}
</style>
