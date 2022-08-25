<template>
  <div class="container">
    <h1>Payment</h1>
    <input type="text" @input="input">
    <input type="text" @input="inputPrice">
    <div class="payment">
      <label for="">{{ item1.name }}</label>
      <label for="">{{ item1.price }}</label>
      <a :href="url1">bought at...</a>
      <button @click="buy(item1.name)">BUY</button>
    </div>
    <div class="payment">
      <label for="">{{ itemName2 }}</label>
      <label for="">{{ price2 }}</label>
      <a :href="url2">bought at...</a>
      <button @click="buy(itemName2)">BUY</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

// const itemName1 = ref<string>('Desk')
const itemName2 = 'Bike'

const item1 = reactive({
  name: 'Desk',
  price: 40000
})

// const price1 = 20000
const price2 = 40000

const url1 = '#'
const url2 = '#'

const buy = (itemName: string) => {
  alert('Are you sure to buy ' + itemName + ' ?')
}

const input = (event: any) => {
  // refはオブジェクトなので、itemName1.valueとすると、constで定義していても再代入できる
  item1.name = event.target.value
}

const inputPrice = (event: any) => {
  item1.price = event.target.value
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin-bottom: 8px;
}

label {
  color: black;
  font-size: 20px;
  font-weight: bold;
}
</style>
