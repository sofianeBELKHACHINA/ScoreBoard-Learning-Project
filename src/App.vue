<script setup>
import { ref } from 'vue'
const playersList = ref([
  {
    id: 1,
    alias: 'Alfred',
    gender: 'male',
    age: 32,
    level: 'Expert',
    numberOfWin: 2,
    actualScore: 0,
  },
  {
    id: 2,
    alias: 'Lisa',
    gender: 'female',
    age: 29,
    level: 'Intermediate',
    numberOfWin: 1,
    actualScore: 0,
  },
])

const pointValueList = [1, 2, 5]
const addPoint = (index, pointValue) => {
  playersList.value[index].actualScore += pointValue
}

const resetScore = () => {
  for (let i = 0; i < playersList.value.length; i++) {
    playersList.value[i].actualScore = 0
  }
}
</script>

<template>
  <main>
    <h1>Scoreboard</h1>
    <div class="boards">
      <section v-for="(playerInfos, index) in playersList" :key="playerInfos.id">
        <h3>{{ playerInfos.alias }}</h3>
        <div class="description">
          <p>{{ playerInfos.age }} ans</p>
          <p>level {{ playerInfos.level }}</p>
        </div>

        <p class="wins">
          {{ playerInfos.gender === 'male' ? 'He' : 'She' }} has already
          <span>{{ playerInfos.numberOfWin }}</span>
          {{ playerInfos.numberOfWin > 1 ? 'victories' : 'victory' }}
        </p>
        <h2>Actual score</h2>
        <p>{{ playerInfos.actualScore }}</p>

        <div class="buttonsBloc">
          <button
            v-for="pointValue in pointValueList"
            :key="pointValue"
            @click="addPoint(index, pointValue)"
          >
            Add {{ pointValue }} points
          </button>
          <!-- <button @click="addPoint(index, 1)">Add 1 point</button>
          <button @click="addPoint(index, 2)">Add 2 points</button>
          <button @click="addPoint(index, 5)">Add 5 points</button> -->
        </div>
      </section>
    </div>
    <button @click="resetScore">reset</button>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  height: 100vh;
  background-color: white;
}
.boards {
  /* border: 1px solid green; */
  width: 100%;
  display: flex;
}

section,
section > div {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
}

section:last-child {
  border-left: 1px solid coral;
}

.description {
  margin: 10px 0 20px 0;
}
.wins {
  margin-bottom: 20px;
}
.wins span {
  color: coral;
}

h2 + p {
  font-size: 40px;
  margin: 15px 0;
  background-color: coral;
  height: 80px;
  width: 80px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.buttonsBloc {
  display: flex;
  flex-direction: row;
  gap: 20px;
}
.buttonsBloc button {
  border: 2px coral solid;
  background-color: white;
  color: coral;
  border-radius: 7px;
  padding: 5px 7px;
}

.buttonsBloc button:hover {
  cursor: pointer;
  background-color: coral;
  color: white;
  scale: 1.2;
  transition: scale 0.3;
}

main > button {
  color: grey;
  border: 1px solid grey;
  background-color: white;
  padding: 5px 7px;
  border-radius: 7px;
}
main > button:hover {
  background-color: coral;
  color: white;
  cursor: pointer;
}

button:active {
  opacity: 0.5;
}
</style>
