<template>
  <v-app>
    <Header class="text-center" />
    <div
      id="app"
      class="main-content text-center"
      src="./assets/background-d.jpg"
    >
      <v-container fill-height>
        <v-row>
          <Team
            v-for="(team, index) in teams"
            :key="index"
            :teamName="team.teamName"
            :score="team.score"
            :getImage="getImage"
            :addPoint="addPoint"
            :subtractPoint="subtractPoint"
            :updateTeamName="updateTeamName"
            :index="index"
          />
        </v-row>
        <v-row>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-btn x-large color="green" dark @click="createNewTeam">
              チームをふやす
            </v-btn>
          </v-col>
          <v-col cols="12" sm="6">
            <v-btn x-large color="orange" dark @click="deleateTeam">
              チームをへらす
            </v-btn>
          </v-col>
        </v-row>
      </v-container>

      <Winner
        v-show="isWinnerModalVisible"
        :winningTeamName="winningTeamName"
        :resetGame="resetGame"
      />
      <div class="modal-overlay" v-show="isWinnerModalVisible"></div>
    </div>
  </v-app>
</template>
<script>
import Header from './components/Header.vue';
import Team from './components/Team.vue';
import Winner from './components/Winner.vue';
export default {
  name: 'app',
  components: {
    Header,
    Team,
    Winner,
  },
  data() {
    return {
      teams: [
        {
          teamName: '',
          score: 0,
        },
        {
          teamName: '',
          score: 0,
        },
      ],
      newTeam: '',
      imageNames: [
        'dino-1.jpg',
        'dino-2.jpg',
        'dino-3.jpg',
        'dino-4.jpg',
        'dino-5.jpg',
        'dino-6.jpg',
        'dino-7.jpg',
        'dino-8.jpg',
        'dino-9.jpg',
        'dino-10.jpg',
        'dino-11.jpg',
        'dino-12.jpg',
        'dino-13.jpg',
        'dino-14.jpg',
        'dino-15.jpg',
        'dino-16.png',
        'dino-17.png',
        'dino-18.png',
        'dino-19.png',
        'dino-20.jpg',
        'dino-21.png',
        'dino-22.png',
        'dino-23.png',
        'dino-24.jpg',
        'dino-25.png',
        'dino-26.png',
        'dino-27.png',
        'dino-28.png',
        'dino-29.png',
        'dino-30.png',
        'dino-31.png',
        'dino-32.jpg',
        'dino-33.jpg',
        'dino-34.png',
        'dino-35.png',
        'dino-36.png',
        'dino-37.png',
        'dino-38.png',
        'dino-39.png',
        'dino-40.png',
      ],
    };
  },
  methods: {
    getImage() {
      let landom = Math.floor(Math.random() * this.imageNames.length);
      return require('@/assets/dinosaur/' + this.imageNames[landom]);
    },
    addPoint(index) {
      this.teams[index].score++;
    },
    subtractPoint(index) {
      if (this.teams[index].score > 0) this.teams[index].score--;
    },
    createNewTeam() {
      this.teams.push({ teamName: this.newTeam, score: 0 });
      this.newTeam = '';
    },
    deleateTeam() {
      this.teams.pop();
    },
    updateTeamName(newTeamName, index) {
      this.teams[index].teamName = newTeamName;
    },
    resetGame() {
      this.teams.forEach((team) => (team.score = 0));
    },
  },
  computed: {
    isWinnerModalVisible() {
      return this.teams.some((team) => team.score > 99);
    },
    winningTeamName() {
      let highestScore = 0;
      this.teams.forEach((team) =>
        team.score > highestScore ? (highestScore = team.score) : highestScore
      );
      return this.teams.find((team) => team.score === highestScore).teamName;
    },
  },
};
</script>
<style>
.main-content {
  background: url(./assets/background-d.jpg);
  background-size: cover;
  background-position: center center;
  width: 100%;
  height: 100%;
}

.add-team {
  margin-right: auto;
  margin-left: auto;
  width: 90%;
}
</style>
