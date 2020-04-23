<template>
  <div class="grid-item">
    <button class="basic-button" @click="roll">Roll</button>
    <div class="face">
      <span
        v-for="(dot, index) in localDie.result"
        :key="index"
        class="pip"
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    die: Object,
    numberOfRolls: Number
  },
  data() {
    return {
      localDie: Object
    }
  },
  created() {
    this.localDie = { ...this.die }
    this.roll()
  },
  methods: {
    roll() {
      this.localDie.result = (1 + 6 * Math.random()) | 0
      this.$emit('diceValue', this.localDie)
    }
  },
  watch: {
    numberOfRolls() {
      this.roll()
    }
  }
}
</script>

<style scoped>
.basic-button:hover {
  background: lightcoral;
  border-color: lightcoral;
}

.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  padding: 20px;
  font-size: 30px;
  text-align: center;
  margin: auto;
}
.face {
  display: grid;
  grid-template-areas:
    'a . c'
    'e g f'
    'd . b';

  flex: 0 0 auto;
  margin: 16px;
  padding: 10px;
  width: 104px;
  height: 104px;

  background-color: #e7e7e7;
  box-shadow: inset 0 5px white, inset 0 -5px #bbb, inset 5px 0 #d7d7d7,
    inset -5px 0 #d7d7d7;
  border-radius: 10%;
}

.pip {
  display: block;
  align-self: center;
  justify-self: center;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  background-color: #333;
  box-shadow: inset 0 3px #111, inset 0 -3px #555;
}

.pip:nth-child(2) {
  grid-area: b;
}
.pip:nth-child(3) {
  grid-area: c;
}
.pip:nth-child(4) {
  grid-area: d;
}
.pip:nth-child(5) {
  grid-area: e;
}
.pip:nth-child(6) {
  grid-area: f;
}
/* This selects the last pip of odd-valued dice (1, 3, 5) and positions the pip in the center */
.pip:nth-child(odd):last-child {
  grid-area: g;
}
</style>
