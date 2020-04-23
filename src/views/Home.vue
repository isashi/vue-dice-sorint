<template>
  <div class="home">
    <button class="basic-button" @click="addDice">Add dice</button>
    <button :class="{ 'basic-button': true }" @click="rollAll">
      Roll all
    </button>
    We rolled all dices {{ numberOfRolls }} times!
    <br />
    Dice: {{ dice }}
    <br />
    Total: {{ total }}
    <div class="grid-container" v-if="dice.length > 0">
      <dice-roller
        v-for="die in dice"
        :key="die.id"
        :die="die"
        :numberOfRolls="numberOfRolls"
        @diceValue="updateDice($event)"
      />
    </div>
  </div>
</template>

<script>
import DiceRoller from '@/components/DiceRoller.vue'

let diceId = 0

export default {
  name: 'Home',
  props: ['num'],
  components: {
    DiceRoller
  },
  data() {
    return {
      dice: [],
      numberOfRolls: 0
    }
  },
  created() {
    console.log(this.num)
    console.log(this.$route.params.num)
    for (var i = 0; i <= this.num - 1; i++) {
      this.addDice()
    }
  },
  computed: {
    total() {
      return this.dice.reduce((a, { result }) => a + result, 0)
    }
  },
  methods: {
    addDice() {
      this.dice.push({ id: ++diceId, result: null })
    },
    rollAll() {
      this.numberOfRolls += 1
    },
    updateDice(diceToUpdate) {
      this.dice.find(item => item.id == diceToUpdate.id).result =
        diceToUpdate.result
    }
  }
}
</script>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto;
  background-color: #ccc;
  padding: 10px;
  margin-top: 10px;
}
</style>
