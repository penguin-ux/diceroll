<template>
  <div class="container">
    <h1>確率の壁</h1>
    <div>
      <div v-for="(result, index) in diceResults" :key="index" class="dice">
        {{ result }}
        <img :src="require(`../assets/img/${fileName}.png`)" />
      </div>
    </div>
    <p>サイコロを振った回数: {{ rollCount }}</p>
    <button @click="rollDice">サイコロを振る</button>
    <p v-if="matchingNumbers" class="clear-text">Clear!</p>
    <div>
      {{ matchResults }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'diceRoll',
  data() {
    return {
      diceResults: [],
      rollCount: 0,
      matchingNumbers: false,
      numDice: 2,
      matchResults: [],
      fileName: "logo1"
    }
  },
  methods: {
    rollDice() {
      this.diceResults = this.generateRandomNumbers(this.numDice)
      this.updateRollCount()
      this.checkMatchingNumbers()
    },
    generateRandomNumbers(numDice) {
      const results = []
      for (let i = 0; i < numDice; i++) {
        const randomNumber = Math.floor(Math.random() * 6) + 1
        results.push(randomNumber)
      }
      return results
    },
    updateRollCount() {
      this.rollCount++
    },
    checkMatchingNumbers() {
      const targetNumber = this.diceResults[0]
      this.matchingNumbers = this.diceResults.every(diceResultNumber => diceResultNumber === targetNumber)
      if (this.matchingNumbers) {
        this.numDice++
        this.matchResults.push(this.rollCount)
        this.rollCount = 0
      }
    }
  }
}
</script>

<style scoped>
.container {
  text-align: center;
  margin: 30px auto;
}

.dice {
  display: inline-block;
  width: 50px;
  height: 50px;
  border: 1px solid black;
  text-align: center;
  line-height: 50px;
  margin-right: 10px;
}

.clear-text {
  font-weight: bold;
  font-size: 20px;
  color: green;
}

</style>
