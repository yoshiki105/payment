<template>
  <div class="container">
    <h1>Payment</h1>
    <input type="text" @input="input">
    <div class="payment">
      <label for="">{{ itemName1 }}</label>
      <label for="">{{ price1 }}</label>
      <a :href="url1">bought at...</a>
      <button @click="buy(itemName1)">BUY</button>
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
const itemName1 = 'Desk'
const itemName2 = 'Bike'

const price1 = 20000
const price2 = 40000

const url1 = '#'
const url2 = '#'

const buy = (itemName: string) => {
  alert('Are you sure to buy ' + itemName + ' ?')
}

const input = (event: any) => {
  console.log(event.target.value)
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
