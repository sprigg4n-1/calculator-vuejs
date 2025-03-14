<script setup lang="ts">
import { ref } from 'vue'
const prevNumber = ref<string>('')
const typedNumber = ref<string>('')
const chosenSign = ref<string>('')
const calculeteRow = ref<string>('')

const onClickChooseSign = (sign: string) => {
  chosenSign.value = sign

  if (typedNumber.value !== '') {
    prevNumber.value = typedNumber.value

    calculeteRow.value = `${prevNumber.value} ${chosenSign.value}`
  }

  typedNumber.value = ''
}

const onClickGetResult = () => {
  if (chosenSign.value !== '') {
    switch (chosenSign.value) {
      case '+':
        prevNumber.value = String(+prevNumber.value + +typedNumber.value)
        break
      case '-':
        prevNumber.value = String(+prevNumber.value - +typedNumber.value)
        break
      case '/':
        prevNumber.value = String(+prevNumber.value / +typedNumber.value)
        break
      case 'x':
        prevNumber.value = String(+prevNumber.value * +typedNumber.value)
        break
    }

    calculeteRow.value = ``
    chosenSign.value = ''
    typedNumber.value = prevNumber.value
  }
}

const onClickSetNumber = (value: string) => {
  if (typedNumber.value === '0') {
    typedNumber.value = value
  } else {
    typedNumber.value += value
  }
}

const onClickReset = () => {
  typedNumber.value = ''
  calculeteRow.value = ''
  prevNumber.value = ''
}

const onClickSlice = () => {
  typedNumber.value = typedNumber.value.slice(0, typedNumber.value.length - 1)
}
</script>

<template>
  <div class="container">
    <div class="calculator">
      <div class="calculator__screen">
        <span class="calculator__screen-top">{{ calculeteRow }}</span>
        <input v-model="typedNumber" class="calculator__screen-bottom" placeholder="0" />
      </div>
      <div class="calculator__buttons">
        <button class="calculator__buttons-btn" @click="onClickReset">CE</button>
        <button class="calculator__buttons-btn btn-2" @click="onClickSlice">⌫</button>
        <button class="calculator__buttons-btn" @click="onClickChooseSign('+')">+</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('1')">1</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('2')">2</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('3')">3</button>
        <button class="calculator__buttons-btn" @click="onClickChooseSign('-')">-</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('4')">4</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('5')">5</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('6')">6</button>
        <button class="calculator__buttons-btn" @click="onClickChooseSign('/')">/</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('7')">7</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('8')">8</button>
        <button class="calculator__buttons-btn" @click="onClickSetNumber('9')">9</button>
        <button class="calculator__buttons-btn" @click="onClickChooseSign('x')">x</button>
        <button class="calculator__buttons-btn btn-2" @click="onClickSetNumber('0')">0</button>
        <button class="calculator__buttons-btn btn-2" @click="onClickGetResult">=</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.calculator {
  background-color: rgb(39, 39, 39);
  padding: 10px;
  border-radius: 10px;
  width: 400px;
  height: fit-content;
  color: white;
}

.calculator__screen {
  display: flex;
  flex-direction: column;
  align-items: end;
  height: fit-content;
  justify-content: space-between;
  margin-bottom: 10px;
  background-color: rgb(85, 85, 85);
  padding: 8px 15px;
  gap: 10px;
}

.calculator__screen-top {
  font-size: 16px;
  color: rgb(182, 182, 182);
}
.calculator__screen-bottom {
  font-size: 24px;
  font-weight: bold;
  background-color: transparent;
  border: none;
  text-align: right;
  color: white;
  padding: 5px 10px;
  width: 100%;
  background-color: rgb(0, 0, 0);
}

.calculator__buttons {
  display: flex;
  flex-wrap: wrap;
}

.calculator__buttons-btn {
  width: 25%;
  border: none;
  height: 70px;
  font-size: 24px;
  border: 1px solid rgb(39, 39, 39);
  cursor: pointer;
  background-color: rgb(168, 168, 168);
}

.calculator__buttons-btn:hover {
  background-color: white;
  transition: 0.3s all;
}

.calculator__buttons-btn.btn-2 {
  width: 50%;
}
</style>
