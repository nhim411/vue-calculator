<template>
  <div class="calculator">
    <div class="wrapper">
      <div class="display">
        <div class="title">
          <div class="title-left">CASIO</div>
          <div class="title-right">Fx - 570ES Plus</div>
        </div>
        <div class="current">Phép tính: {{ current || "0" }}</div>
        <div class="result">Kết quả: {{ result || "0" }}</div>
      </div>
      <div class="btn-group">
        <div class="btn" @click="clear">AC</div>
        <div class="btn" @click="clearOne">C</div>
        <div class="btn"></div>
        <div class="btn" @click="add">+</div>
        <div class="btn" @click="append('7')">7</div>
        <div class="btn" @click="append('8')">8</div>
        <div class="btn" @click="append('9')">9</div>
        <div class="btn" @click="minus">-</div>
        <div class="btn" @click="append('4')">4</div>
        <div class="btn" @click="append('5')">5</div>
        <div class="btn" @click="append('6')">6</div>
        <div class="btn" @click="times">x</div>
        <div class="btn" @click="append('1')">1</div>
        <div class="btn" @click="append('2')">2</div>
        <div class="btn" @click="append('3')">3</div>
        <div class="btn" @click="divide">/</div>
        <div class="btn" @click="append('0')">0</div>
        <div class="btn" @click="dot">.</div>
        <div class="btn" @click="equal">=</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalculatorApp",
  data() {
    return {
      previous: null,
      result: null,
      current: "",
      operator: null,
      operatorClicked: false,
    };
  },
  methods: {
    clear() {
      this.current = "";
      this.result = "";
    },
    append(number) {
      this.current = `${this.current}${number}`;
    },
    add() {
      this.current = `${this.current}+`;
    },
    minus() {
      this.current = `${this.current}-`;
    },
    divide() {
      this.current = `${this.current}/`;
    },
    times() {
      this.current = `${this.current}*`;
    },
    dot() {
      this.current = `${this.current}.`;
    },
    clearOne() {
      this.current = this.current.slice(0, this.current.length - 1);
    },
    equal() {
      let operatorTrue = true;
      let result;
      try {
        result = eval(this.current);
      } catch (e) {
        operatorTrue = false;
      }
      if (operatorTrue) {
        console.log(`${this.current} = ${eval(this.current)}`);
        this.result = result;
        this.current = "";
      } else {
        alert("Phép tính sai");
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*,
*::before,
*::after {
  box-sizing: border-box;
}
* {
  margin: 0;
}

html,
body {
  height: 100%;
}
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}

img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
}
input,
button,
textarea,
select {
  font: inherit;
  outline: none;
  border: none;
}
p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
}

.calculator {
  display: flex;
  justify-content: center;
  align-items: center;
}

.wrapper {
  background-color: rgb(39, 116, 204);
  padding: 10px;
  border-radius: 4px;
}

.btn-group {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(5, 1fr);
  grid-column-gap: 10px;
  grid-row-gap: 10px;
  background-color: #fff;
  padding: 10px;
  border-radius: 4px;
}

.btn {
  padding: 16px 26px;
  border: 1px solid black;
  cursor: pointer;
  background-color: rgb(239, 239, 239);
}

.display {
  background-color: rgb(250, 235, 215);
  border-radius: 4px;
  padding: 16px 8px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 180px;
  margin-bottom: 10px;
  /* box-shadow: 5px 5px 5px 2px black inset; */
  z-index: 2;
}

.result,
.current {
  font-size: 20px;
  font-weight: bold;
}

.result {
  align-self: flex-end;
}

.current {
  align-self: flex-start;
}

.title {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  width: 100%;
}

.title-left {
  font-weight: bold;
}

.title-left {
  color: rgb(159, 139, 137);
}
</style>
