<script setup>
import { ref, computed } from 'vue';

const x = ref(0);
const y = ref(0);
const selectedOp = ref('+');
const operators = ['+', '-', '*', '/', '%'];

const result = computed(() => {
  const a = Number(x.value);
  const b = Number(y.value);
  switch (selectedOp.value) {
    case '+':
      return a + b;
    case '-':
      return a - b;
    case '*':
      return a * b;
    case '/':
      return a / b; // JS returns Infinity or NaN as appropriate
    case '%':
      return a % b; // JS returns NaN for modulus by zero
    default:
      return NaN;
  }
});
</script>

<template>
  <div>
    <p>x <input v-model.number="x" type="number" /></p>
    <select v-model="selectedOp">
      <option v-for="op in operators" :key="op" :value="op">{{ op }}</option>
    </select>
    <p>y <input v-model.number="y" type="number" /></p>
    <p>---------------------</p>
    <p>= {{ result }}</p>
  </div>
</template>

<style scoped>
p,
input {
  font-family: monospace;
}
p {
  white-space: pre;
}
</style>
