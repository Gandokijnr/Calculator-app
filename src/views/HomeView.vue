<template>
  <main class="bg-gray-900 p-12">
    <div class="flex justify-center rounded">
      <div class="wrapper bg-gray-800 rounded-t-lg rounded-b-lg">
        <div class="calculator bg-gray-300 h-40 rounded-b-3xl rounded-t-lg flex flex-col justify-between p-8 m-4">
          <p class="flex justify-start font-bold text-5xl"> {{ result }} </p>
          <p class="flex justify-end font-bold text-3xl"> {{ expression }} </p>
      </div>
      <div class="calculator bg-gray-800 w-96 h-96 rounded-t-3xl rounded-b-lg mt-12 row px-8">
        <div class="col flex justify-around gap-4 text-center mb-4">
          <span class="p-3 px-5 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="clear_all_expression()">AC</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('%')">%</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="clear_expression()">C</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('/')">/</span>
        </div>
        <div class="col flex justify-around gap-4 text-center mb-4">
          <span class="p-3 px-5 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('9')">9</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('8')">8</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('7')">7</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('*')">*</span>
        </div>
        <div class="col flex justify-around gap-4 text-center mb-4">
          <span class="p-3 px-5 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('6')">6</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('5')">5</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('4')">4</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('-')">-</span>
        </div>
        <div class="col flex justify-around gap-4 text-center mb-4">
          <span class="p-3 px-5 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('3')">3</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('2')">2</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('1')">1</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('+')">+</span>
        </div>
        <div class="col flex justify-around gap-4 text-center mb-4">
          <span class="p-3 px-5 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('00')">00</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('0')">0</span>
          <span class="p-3 px-7 text-2xl bg-gray-400 rounded-full cursor-pointer" @click="appendToExpression('.')">.</span>
          <span class="p-3 px-7 text-2xl bg-red-400 rounded-full cursor-pointer" @click="addExpression()">=</span>
        </div>
      </div>
      </div>
    </div>
  </main>
</template>


<script>
export default {
  data() {
    return {
      expression: '',
      result: '',
    }
  },
  methods: {
    appendToExpression(character) {
      this.expression += character;      
    },
    addExpression() {
      this.result = eval(this.expression);
    },
    clear_expression() {
      this.expression = '';
    },
    clear_all_expression() {
      this.expression = '';
      this.result = '';
    },
    evaluateExpression() {
      try {
        this.expression = eval(this.expression);
      } catch (error) {
        this.expression = 'Error';
      }
    },
  }
}
</script>

<style>
span {
  width: 30%!important;
  height: 30%!important;
}
</style>