<script setup>
import { reactive } from "vue";

const estado = reactive({
  operator: "",
  num1: "",
  num2: "",
  result: ""
});

const sub = ({ num1, num2 }) => num1 - num2;
const add = ({ num1, num2 }) => num1 + num2;
const mult = ({ num1, num2 }) => num1 * num2;
const div = ({ num1, num2 }) => num1 / num2;

function capturaValor1(evento) {
  estado.num1 = evento.target.value;
}

function capturaValor2(evento) {
  estado.num2 = evento.target.value;
}

function capturaOperador(evento) {
  estado.operator = evento.target.value;
}

const result = () => {
  const { num1, num2, operator } = estado;
  if (num1 !== "" && num2 !== "") {
    switch (operator) {
      case "+":
        return add({ num1: parseFloat(num1), num2: parseFloat(num2) });
      case "-":
        return sub({ num1: parseFloat(num1), num2: parseFloat(num2) });
      case "x":
        return mult({ num1: parseFloat(num1), num2: parseFloat(num2) });
      case "÷":
        return div({ num1: parseFloat(num1), num2: parseFloat(num2) });
      default:
        return "";
    }
  }
  return "";
};

function Calculate(value, type) {
  if (type === "number") {
    if (estado.operator === "") {
      estado.num1 = estado.num1.toString() + value.toString();
    } else {
      estado.num2 = estado.num2.toString() + value.toString();
    }
  } else if (type === "operator") {
    estado.operator = value;
  } else if (type === "=" && value === "=") {
    estado.result = result();
  } else if (type === "ac" && value === "AC") {
    estado.num1 = "";
    estado.num2 = "";
    estado.operator = "";
    estado.result = "";
  }
}
</script>

<template>
  <div class="calculator">
    <form class="form_calculator">
      <fieldset class="form_calculator-screem">
        <legend class="legend">Calculator</legend>
        <input
          type="text"
          class="screem"
          :value="estado.result !== '' ? estado.result : `${estado.num1} ${estado.operator} ${estado.num2}`"
          disabled
        />
        <div class="grup">
          <input
            type="reset"
            class="button"
            @click="Calculate('AC', 'ac')"
            name="ac"
            value="AC"
          />
          <input
            type="button"
            class="button"
            @click="Calculate('÷', 'operator')"
            name="divide"
            value="÷"
          />
        </div>
        <div class="grup">
          <input
            type="button"
            class="button"
            @click="Calculate(7, 'number')"
            name="7"
            value="7"
          />
          <input
            type="button"
            class="button"
            @click="Calculate(8, 'number')"
            name="8"
            value="8"
          />
          <input
            type="button"
            class="button"
            @click="Calculate(9, 'number')"
            name="9"
            value="9"
          />
          <input
            type="button"
            class="button"
            @click="Calculate('x', 'operator')"
            name="multiplication"
            value="x"
          />
        </div>
        <div class="grup">
          <input
            type="button"
            class="button"
            @click="Calculate(4, 'number')"
            name="number_4"
            value="4"
          />
          <input
            type="button"
            class="button"
            @click="Calculate(5, 'number')"
            name="number_5"
            value="5"
          />
          <input
            type="button"
            class="button"
            @click="Calculate(6, 'number')"
            name="number_6"
            value="6"
          />
          <input
            type="button"
            class="button"
            @click="Calculate('-', 'operator')"
            name="-"
            value="-"
          />
        </div>
        <div class="grup">
          <input
            type="button"
            class="button"
            @click="Calculate(1, 'number')"
            name="1"
            value="1"
          />
          <input
            type="button"
            class="button"
            @click="Calculate(2, 'number')"
            name="2"
            value="2"
          />
          <input
            type="button"
            class="button"
            @click="Calculate(3, 'number')"
            name="3"
            value="3"
          />
          <input
            type="button"
            class="button"
            @click="Calculate('+', 'operator')"
            name="+"
            value="+"
          />
        </div>
        <div class="grup">
          <input
            type="button"
            class="button-center"
            @click="Calculate(0, 'number')"
            name="0"
            value="0"
          />
          <input
            type="button"
            class="button"
            @click="Calculate('.', 'number')"
            name="."
            value="."
          />
          <input
            type="button"
            class="button-center"
            @click="Calculate('=', '=')"
            name="="
            value="="
          />
        </div>
      </fieldset>
    </form>
  </div>
</template>

<style scoped>
.container {
  margin: 0 auto;
}

.calculator {
  background: rgb(174, 174, 202);
  padding: 0;
  margin-top: 50px;
  border-radius: 20px;
  text-align: center;
}

.form_calculator {
  padding: 50px;
}

.form_calculator-screem {
  display: inline-block;
  width: 300px;
}

.screem {
  padding: 10px;
  margin: 10px;
  font-size: 21px;
  text-align: right;
  border: solid 1px #000;
  box-shadow: 1px 1px 1px #000;
}

.button {
  width: 60px;
  height: 50px;
  margin: 5px;
  padding: 2px;
  background: rgba(228, 222, 222, 0.4);
  border: 1px solid rgba(228, 222, 222, 0.4);
}

.button-center {
  width: 95px;
  height: 50px;
  margin: 5px;
  background: rgba(228, 222, 222, 0.4);
  border: 1px solid rgba(228, 222, 222, 0.4);
}

.button:hover {
  background-color: rgba(94, 100, 187, 0.74);
  border: none;
}
</style>
