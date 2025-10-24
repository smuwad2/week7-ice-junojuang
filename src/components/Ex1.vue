<script>
export default {
  data() {
    return {
      x: 0,
      y: 0,
      selectedOp: '+',
      operators: ['+', '-', '*', '/', '%']
    }
  },
  computed: {
    // compute the result of x (op) y without using eval
    result() {
      const a = Number(this.x)
      const b = Number(this.y)
      switch (this.selectedOp) {
        case '+':
          return a + b
        case '-':
          return a - b
        case '*':
          return a * b
        case '/':
          return b === 0 ? '∞' : a / b
        case '%':
          return b === 0 ? 'NaN' : a % b
        default:
          return 'NaN'
      }
    }
  }
}
</script>

<template>
  <div>
    <p>x <input v-model.number="x" /></p>
    <p>operator 
      <select v-model="selectedOp">
        <option v-for="op in operators" :key="op" :value="op">{{ op }}</option>
      </select>
    </p>
    <p>y <input v-model.number="y" /></p>
    <p>=</p>
    <p>{{ result }}</p>
  </div>
</template>
