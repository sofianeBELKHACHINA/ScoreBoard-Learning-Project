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

const addOne = (index) => {
  playersList.value[index].actualScore += 1
}

const addTwo = (index) => {
  playersList.value[index].actualScore += 2
}

const addFive = (index) => {
  playersList.value[index].actualScore += 5
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
        <h2>Actual score</h2>
        <p>{{ playerInfos.actualScore }}</p>
        <div>
          <button @click="addOne(index)">Add 1 point</button>
          <button @click="addTwo(index)">Add 2 points</button>
          <button @click="addFive(index)">Add 5 points</button>
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
  background-color: pink;
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
</style>
