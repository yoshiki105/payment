<template>
  <div class="container">
    <h1>Payment</h1>
    <input type="text" v-model="item1.name">
    <input type="text" v-model="item1.price">
    <div class="payment">
      <label for="">{{ item1.name }}</label>
      <label for="">{{ priceLabel }}</label>
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
import { ref, reactive, computed, watch, toRefs } from 'vue'

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

// const clear = () => {
//   item1.name = ''
//   item1.price = 0
// }

const budget = 50000

const priceLabel = computed(() => {
  if (item1.price <= budget) {
    return item1.price
  } else {
    return 'too explensive ...'
  }
})

// 以下のようにwatchでも書ける！でも
// const priceLabel = ref<string>(item1.price + ' yen')
// // toRefsはitem1の中のプロパティをそれぞれリアクティブな値にして返す
// //   => item1.priceをリアクティブな定数priceに代入
// const { price } = toRefs(item1)
// // watchの第一引数はリアクティブな値をとるので、item1.priceとしたらダメ。item1はリアクティブだけど、そのプロパティであるpriceはリアクティブではないため。
// // そこでtoRefsを使って、priceをリアクティブな値を指定する。
// watch(price, () => {
//   // watchでは第一引数が変更されると、第二引数の関数が実行される
//   if (item1.price <= budget) {
//     priceLabel.value = item1.price + ' yen'
//   } else {
//     priceLabel.value = 'too explensive ...'
//   }
// })
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
