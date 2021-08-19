<template>
  <v-col cols="12" sm="6" md="4" lg="3">
    <div>
      <v-card class="mx-auto" max-width="400">
        <v-img
          class="white--text align-end"
          height="300px"
          v-bind:src="getImage(index)"
        >
          <v-card-title class="img-title text-h4">{{ teamName }}</v-card-title>
        </v-img>

        <v-card-subtitle class="pb-0">
          <v-text-field
            label="チームめい"
            placeholder="チームめい"
            outlined
            v-model="newTeamName"
            @keyup="updateTeamName(newTeamName, index)"
          ></v-text-field>
        </v-card-subtitle>

        <v-card-text class="text--primary">
          <div class="text-h2">{{ score }}</div>
        </v-card-text>

        <v-card-actions>
          <v-btn class="mx-2" fab dark color="indigo" @click="addPoint(index)">
            <v-icon dark>
              mdi-plus
            </v-icon>
          </v-btn>
          <v-btn
            class="mx-2"
            fab
            dark
            color="red"
            @click="subtractPoint(index)"
          >
            <v-icon dark>
              mdi-minus
            </v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </v-col>
</template>

<script>
export default {
  name: 'Team',
  props: {
    teamName: String,
    score: Number,
    getImage: Function,
    addPoint: Function,
    subtractPoint: Function,
    updateTeamName: Function,
    index: Number,
  },
  data() {
    return {
      newTeamName: this.teamName,
    };
  },
};
</script>

<style scoped>
.score {
  margin-top: 1rem;
  font-size: 1.5rem;
}

.img-title {
  color: black;
  background-color: rgba(255, 255, 255, 0.5);
}
</style>
