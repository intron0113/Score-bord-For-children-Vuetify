<template>
  <div>
    <h1>Congratulations!</h1>
    <p class="text-h4">{{ winningTeamName }} won the game!!</p>
    <v-btn rounded color="orange" dark @click="resetGame">ゲームリセット</v-btn>
  </div>
</template>

<script>
export default {
  name: 'Winner',
  props: {
    winningTeamName: String,
    resetGame: Function,
  },
};
</script>

<style scoped>
div {
  background-color: #99ddff;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 10;
  height: 350px;
  width: 550px;
  border: 1px solid grey;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
