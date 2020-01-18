<template>
  <div class="calculator">
    <div class="display">123456</div>
    <div class="btn">C</div>
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div class="btn">/</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn">X</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn">+</div>
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn">=</div>
  </div>
</template>

<script>
export default {
  name: "Calculator"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  grid-column: 1/5;
  background-color: lightblue;
}

.zero {
  grid-column: 1/3;
}
</style>
