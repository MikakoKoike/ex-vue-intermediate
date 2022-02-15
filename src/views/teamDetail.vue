<template>
  <div class="detail">
    <table>
      <tr>
        <th>球団名</th>
        <td>
          <span>{{ currentTeam.teamName }}</span>
        </td>
      </tr>
      <th>本拠地</th>
      <td>
        <span>{{ currentTeam.headquarters }}</span>
      </td>
      <tr>
        <th>発足日</th>
        <td>
          <span>{{ currentTeam.inauguration }}</span>
        </td>
      </tr>
      <tr>
        <th>歴史</th>
        <td>
          <span>{{ currentTeam.history }}</span>
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
   * VuexストアのGetter経由で受け取ったIDから1件のみチーム情報を取得する
   */
  created(): void {
    const teamId = Number(this.$route.params.id);
    this.currentTeam = this.$store.getters.getTeamsById(teamId);
  }
}
</script>

<style scoped>
.detail {
  text-align: left;
}
</style>
