<template>
  <div class="flexbox">
    <div class="calculator">
      <div class="display">{{current || '0'}}</div>
      <div class="btn dark" @click="clear">C</div>
      <div class="btn dark" @click="sign">+/-</div>
      <div class="btn dark" @click="percent">%</div>
      <div class="btn operator" @click="divide">/</div>
      <div class="btn" @click="append('7')">7</div>
      <div class="btn" @click="append('8')">8</div>
      <div class="btn" @click="append('9')">9</div>
      <div class="btn operator" @click="multiply">x</div>
      <div class="btn" @click="append('4')">4</div>
      <div class="btn" @click="append('5')">5</div>
      <div class="btn" @click="append('6')">6</div>
      <div class="btn operator" @click="minus">-</div>
      <div class="btn" @click="append('1')">1</div>
      <div class="btn" @click="append('2')">2</div>
      <div class="btn" @click="append('3')">3</div>
      <div class="btn operator" @click="plus">+</div>
      <div class="btn zero" @click="append('0')">0</div>
      <div class="btn" @click="dot">.</div>
      <div class="btn operator" @click="equal">=</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      current: "1234",
      previous: "",
      operator: null,
      operatorClicked: false,
      animateCss: ["animated", "flash", "slower", "infinite"]
    };
  },
  watch: {
    current: {
      immediate: true,
      handler() {
        const display = document.querySelector(".display");
        if (this.current.length > 10) {
          this.current = this.current.slice(0, 10);
        }
        if (this.current === "") {
          display.classList.add(...this.animateCss);
        } else {
          display.classList.remove(...this.animateCss);
        }
      }
    }
  },
  methods: {
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    clear() {
      this.current = "";
      this.operator = null;
      this.operatorClicked = false;
    },
    percent() {
      this.result = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) this.current = "";
      this.current =
        this.current === "0" ? `${number}` : `${this.current}${number}`;
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    plus() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;
      this.operator = null;
      this.operatorClicked = false;
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.flexbox {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
}

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
  text-align: right;
  padding-right: 20px;
  background-color: #222;
  color: #ffffff;
}

.btn {
  border: 1px solid black;
  background-color: #999;
  cursor: pointer;
  border-radius: 40px;
  margin: 10px;
  color: #222;
  font-weight: bold;
}

.dark {
  background-color: #333;
  color: #ffffff;
}

.operator {
  background-color: #e08d1f;
}
.zero {
  grid-column: 1/3;
}
</style>
