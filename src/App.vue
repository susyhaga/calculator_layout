<script setup>
import { reactive } from "vue";
import Screen from './components/Screen.vue';
import Buttons from './components/Buttons.vue';


const estado = reactive({
  operator: "",
  num1: "",
  num2: "",
  result: ""
});

const sub = ({ num1, num2 }) => num1 - num2;
const add = ({ num1, num2 }) => num1 + num2;
const mult = ({ num1, num2 }) => num1 * num2;
const div = ({ num1, num2 }) => {
  const result = num1 / num2;
  if (!isFinite(result)) {
    return "Error! ÷ by 0 is not allowed";
  } else {
    return result;
  }
};


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
  <div class="container">
    <div class="calculator">
      <form class="form_calculator">
        <fieldset class="form_calculator-screen">
          <legend class="legend">Calculator</legend>
          <Screen :result="estado.result" :num1="estado.num1" :operator="estado.operator" :num2="estado.num2" />
          <Buttons :calculate="Calculate" />
        </fieldset>
      </form>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 70%;
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
  padding: 20px;
}

.form_calculator-screen {
  display: inline-block;
  width: 300px;
}

.legend {
  margin: 0;
  padding: 0;
}

@media (max-width: 600px) {
  
  .calculator {
    
    border-radius: 10px;
  }
  .form_calculator {
    padding: 20px;
    
  }

  .form_calculator-screem {
    width: 90%;
  
  }

  .screem {
    width: calc(100% - 20px);
    font-size: 18px;
    padding: 8px;
    margin: 5px;
  }
}
</style>
