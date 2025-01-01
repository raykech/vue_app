<template>
  <FrontendLayout>
    <Head title="Calculator" />
    <div class="calculator">
      <input type="text" v-model="display" disabled />
      <div class="buttons">
        <button @click="appendNumber('1')">1</button>
        <button @click="appendNumber('2')">2</button>
        <button @click="appendNumber('3')">3</button>
        <button @click="appendNumber('4')">4</button>
        <button @click="appendNumber('5')">5</button>
        <button @click="appendNumber('6')">6</button>
        <button @click="appendNumber('7')">7</button>
        <button @click="appendNumber('8')">8</button>
        <button @click="appendNumber('9')">9</button>
        <button @click="appendNumber('0')">0</button>
        <button @click="appendOperator('+')">+</button>
        <button @click="appendOperator('-')">-</button>
        <button @click="appendOperator('*')">*</button>
        <button @click="appendOperator('/')">/</button>
        <button @click="clearDisplay">C</button>
        <button @click="calculateResult">=</button>
      </div>
    </div>
  </FrontendLayout>
</template>

<script setup>
import { ref } from 'vue';
import FrontendLayout from '@/Layouts/FrontendLayout.vue';
import { Head } from '@inertiajs/vue3';

const display = ref('');

const appendNumber = (number) => {
  display.value += number;
};

const appendOperator = (operator) => {
  display.value += ` ${operator} `;
};

const clearDisplay = () => {
  display.value = '';
};

const calculateResult = () => {
  try {
    display.value = eval(display.value.replace(/ /g, ''));
  } catch (e) {
    display.value = 'Error';
  }
};
</script>

<style scoped>
.calculator {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
}

input {
  width: 100%;
  height: 50px;
  font-size: 24px;
  text-align: right;
  margin-bottom: 10px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  height: 50px;
  font-size: 24px;
}
</style>