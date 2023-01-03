
<template>
  <h1></h1>
  <div class="output">
    <div class="outputCalc">{{ calculatorValue || 0 }}</div>
  </div>
  <div class="buttons">
    <div
      class="button"
      v-for="n in btnArr"
      :key="n"
      :class="{ operator: ['C', '*', '/', '-', '+', '%', '='].includes(n) }"
    >
      <div class="btn" @click="action(n)">
        {{ n }}
      </div>
    </div>
  </div>
  <footer>
    Made by:
    <p id="para">Khashayar Shomali</p>
  </footer>
  
</template>

<script>
export default {
  data() {
    return {
      calculatorValue: "",
      btnArr: [
        "C",
        "*",
        "/",
        "-",
        "7",
        "8",
        "9",
        "+",
        "4",
        "5",
        "6",
        "%",
        "1",
        "2",
        "3",
        "=",
        "0",
        ".",
      ],
      operator: null,
      previousCalculatorValue: "",
    };
  },
  methods: {
    action(n) {
      
      if (!isNaN(n) || n === ".") {
        this.calculatorValue += n + "";
      }
      
      if (n === "C") {
        this.calculatorValue = "";
      }
      
      if (n === "%") {
        this.calculatorValue = this.calculatorValue / 100 + "";
      }
      
      if (["/", "*", "-", "+"].includes(n)) {
        this.operator = n;
        this.previousCalculatorValue = this.calculatorValue;
        this.calculatorValue = "";
      }
     
      if (n === "=") {
        this.calculatorValue = eval(
          this.previousCalculatorValue + this.operator + this.calculatorValue
        );
        this.previousCalculatorValue = "";
        this.operator = null;
      }
    },
  },
};
</script>


<style>

@import url(https://fonts.googleapis.com/css2?family=Vazirmatn:wght@600&display=swap);


h1 {
  margin-top: 100px;
  text-align: center;
}

.output {
  text-align: right;
  background-color: #428aff 138, 255;
  width: min(300px, 70%);
  margin: 10px auto;
  padding: 10px;
  border: 0.5px solid rgb(124, 170, 255);
  border-radius: 4px;
  box-shadow: 2.8px 2.8px 2.2px rgba(0, 0, 0, 0.008),
    6.7px 6.7px 5.3px rgba(0, 0, 0, 0.012),
    12.5px 12.5px 10px rgba(0, 0, 0, 0.015),
    22.3px 22.3px 17.9px rgba(0, 0, 0, 0.018),
    41.8px 41.8px 33.4px rgba(0, 0, 0, 0.022),
    100px 100px 80px rgba(0, 0, 0, 0.03);
}
.outputCalc {
  background-color: rgb(148, 210, 255);
  padding: 15px;
  border-radius: 3px;
}
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  width: min(300px, 70%);
  border: 0.2px solid (#428aff 138, 255);
  border-radius: 4px;
  align-items: center;
  background-color: rgb(148, 210, 255);
  justify-content: center;
  margin: 10px auto;
  gap: 5px;
  box-shadow: 2.8px 2.8px 2.2px rgba(0, 0, 0, 0.008),
    6.7px 6.7px 5.3px rgba(0, 0, 0, 0.012),
    12.5px 12.5px 10px rgba(0, 0, 0, 0.015),
    22.3px 22.3px 17.9px rgba(0, 0, 0, 0.018),
    41.8px 41.8px 33.4px rgba(0, 0, 0, 0.022),
    100px 100px 80px rgba(0, 0, 0, 0.03);
}
.button {
  background-color:rgb(255, 255, 255);
  padding: 6px;
  border-radius: 3px;
  margin: 4px;
  font-size: 1.5em;
  font-weight: bold;
  color: #000;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}
.button:hover {
  background-color: rgb(29, 142, 255);
  color: #000;
}
.operator {
  background-color: rgb(204, 234, 255);
  color: #000;
}
.operator:hover {
  background-color: rgb(29, 142, 255);
}
.MyId:hover {
  cursor: pointer;
  filter: brightness(130%);
}
footer {
  text-align: center;
  width: min(300px, 90%);
  border-radius: 3px;
  margin: 72px auto;
  background-color:rgb(0, 83, 226);
  padding: 10px;
  font-weight: bold;
  color: rgb(255, 255, 255);
  text-transform: capitalize;
  box-shadow: 2.8px 2.8px 2.2px rgba(0, 0, 0, 0.008),
    6.7px 6.7px 5.3px rgba(0, 0, 0, 0.012),
    12.5px 12.5px 10px rgba(0, 0, 0, 0.015),
    22.3px 22.3px 17.9px rgba(0, 0, 0, 0.018),
    41.8px 41.8px 33.4px rgba(0, 0, 0, 0.022),
    100px 100px 80px rgba(0, 0, 0, 0.03);
}

</style>
