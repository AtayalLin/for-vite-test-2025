<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>品項</th>
          <th>描述</th>
          <th>價格</th>
          <th>庫存</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="item in drinks" :key="item.id">
          <td>
            <!-- 編輯按鈕放在名稱前面 -->
            <template v-if="currentDrink && currentDrink.id === item.id">
              <button @click="confirmEdit">儲存</button>
              <button @click="cancelEdit">取消</button>
              <input v-model="currentDrink.tempName" type="text" />
            </template>
            <template v-else>
              <button @click="startEdit(item.id)">編輯</button>
              {{ item.name }}
            </template>
          </td>
          <td>{{ item.content }}</td>
          <td>{{ item.price }}</td>
          <td>
            <button @click="teaNumber(item.id, item.stock - 1)" :disabled="item.stock < 1">
              -
            </button>
            {{ item.stock }}
            <button @click="teaNumber(item.id, item.stock + 1)">+</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const teadata = [
  {
    id: 1,
    name: '珍珠奶茶',
    content: '香濃奶茶搭配QQ珍珠',
    price: 50,
    stock: 20,
  },
  {
    id: 2,
    name: '冬瓜檸檬',
    content: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 15,
  },
  {
    id: 3,
    name: '翡翠檸檬',
    content: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 30,
  },
  {
    id: 4,
    name: '四季春茶',
    content: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10,
  },
  {
    id: 5,
    name: '阿薩姆奶茶',
    content: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25,
  },
  {
    id: 6,
    name: '檸檬冰茶',
    content: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20,
  },
  {
    id: 7,
    name: '芒果綠茶',
    content: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18,
  },
  {
    id: 8,
    name: '抹茶拿鐵',
    content: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20,
  },
]

const drinks = ref(teadata)
const currentDrink = ref(null)

function teaNumber(id, stock) {
  const drink = drinks.value.find((item) => item.id === id)
  if (drink) {
    drink.stock = stock
  }
}

function startEdit(id) {
  const drink = drinks.value.find((item) => item.id === id)
  if (drink) {
    currentDrink.value = { ...drink } // 複製當前飲品資料
  }
}

function confirmEdit() {
  if (currentDrink.value) {
    const updatedDrink = drinks.value.find((item) => item.id === currentDrink.value.id)
    if (updatedDrink) {
      updatedDrink.name = currentDrink.value.tempName
    }
    currentDrink.value = null // 退出編輯模式
  }
}

function cancelEdit() {
  currentDrink.value = null // 退出編輯模式
}
</script>

<style scoped>
/* 美化按鈕樣式 */
button {
  margin-left: 10px;
}
input {
  padding: 5px;
  margin-right: 10px;
}
</style>
