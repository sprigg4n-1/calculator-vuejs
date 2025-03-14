<script setup lang="ts">
import { ref } from 'vue'
import ButtonComponent from './components/ButtonComponent.vue'
import InputComponent from './components/InputComponent.vue'

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
        <InputComponent :value="typedNumber" />
      </div>
      <div class="calculator__buttons">
        <ButtonComponent value="CE" @click="onClickReset" />
        <ButtonComponent value="⌫" is-big @click="onClickSlice" />
        <ButtonComponent value="+" @click="onClickChooseSign('+')" />
        <ButtonComponent value="1" @click="onClickSetNumber('1')" />
        <ButtonComponent value="2" @click="onClickSetNumber('2')" />
        <ButtonComponent value="3" @click="onClickSetNumber('3')" />
        <ButtonComponent value="-" @click="onClickChooseSign('-')" />
        <ButtonComponent value="4" @click="onClickSetNumber('4')" />
        <ButtonComponent value="5" @click="onClickSetNumber('5')" />
        <ButtonComponent value="6" @click="onClickSetNumber('6')" />
        <ButtonComponent value="-" @click="onClickChooseSign('/')" />
        <ButtonComponent value="7" @click="onClickSetNumber('7')" />
        <ButtonComponent value="8" @click="onClickSetNumber('8')" />
        <ButtonComponent value="9" @click="onClickSetNumber('9')" />
        <ButtonComponent value="x" @click="onClickChooseSign('x')" />
        <ButtonComponent value="0" is-big @click="onClickSetNumber('0')" />
        <ButtonComponent value="=" is-big @click="onClickGetResult" />
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

.calculator__buttons {
  display: flex;
  flex-wrap: wrap;
}
</style>
