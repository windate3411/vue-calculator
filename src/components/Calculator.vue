<template>
  <div class="calculator">
    <div class="display">{{result || '0'}}</div>
    <div class="btn" @click="result=0">C</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percent">%</div>
    <div class="btn operator">/</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">X</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      result: "1234"
    };
  },
  methods: {
    sign() {
      this.result =
        this.result.charAt(0) === "-"
          ? this.result.slice(1)
          : `-${this.result}`;
    },
    percent() {
      this.result = `${parseFloat(this.result) / 100}`;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator {
  display: grid;
  width: 400px;
  margin: 0 auto;
  font-size: 40px;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  grid-column: 1/5;
  background-color: lightblue;
}

.btn {
  border: 1px solid black;
  background-color: #999;
  cursor: pointer;
}

.operator {
  background-color: yellow;
}
.zero {
  grid-column: 1/3;
}
</style>
