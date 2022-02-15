<template>
  <div class="detail">
    <table>
      <tr>
        <th>球団名</th>
      </tr>
      <tr>
        <td>
          <span>{{ currentTeam.teamName }}</span>
        </td>
      </tr>
      <tr>
        <th>本拠地</th>
      </tr>
      <tr>
        <td>
          <span>{{ currentTeam.headquarters }}</span>
        </td>
      </tr>
      <tr>
        <th>発足日</th>
      </tr>
      <tr>
        <td>
          <span>{{ currentTeam.formatInauguration }}</span>
        </td>
      </tr>
      <tr>
        <th>歴史</th>
      </tr>
      <tr>
        <td>
          <pre>{{ currentTeam.history }}</pre>
        </td>
      </tr>
    </table>
    <router-link to="/Ex01">
      <button type="button">戻る</button>
    </router-link>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Team } from "@/types/team";

@Component
export default class teamsDetail extends Vue {
  private currentTeam = new Team(0, "", "", new Date(), "");
  /**
   * VuexストアのGetter経由で受け取ったIDから1件のみチーム情報を取得する.
   */
  created(): void {
    const teamId = Number(this.$route.params.id);
    //VuexストアのGetter,getTeamsById()メゾッドにteamIdを渡し、
    //1件のチーム情報を取得し戻り値をcurrentTeamに代入する
    this.currentTeam = this.$store.getters.getTeamsById(teamId);
    console.dir(JSON.stringify(this.currentTeam));
  }
}
</script>

<style scoped>
.detail {
  text-align: left;
}
</style>
