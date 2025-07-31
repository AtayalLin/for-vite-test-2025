<script setup>
import { ref } from 'vue'

const num = ref(0)
const htmltemplate = '<h1>這是 html 片段</h1>'

setInterval(() => {
  num.value++
}, 500)

// v-for ---------------
// const array = ref([
//   {
//     id: '1',
//     name: '小明',
//     age: 18,
//   },
//   {
//     id: '2',
//     name: '小美',
//     age: 16,
//   },
//   {
//     id: '3',
//     name: '阿王',
//     age: 20,
//   },
// ])

// v-if, v-else, v-show--------------------
// const isChecked = ref(false)

// v-on -------------
// const handleClick = () => {
//   console.log('我被觸發了')
// }

// const submitFrom = () => {
//   console.log('表單觸發了')
// }

// const text = ref('文字')
// v-model -------------
// const imgUrl = ref(
//   'https://images.unsplash.com/photo-1545830284-1777ef6d3791?q=80&w=800&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA==',
// )
// const isChecked = ref(false)

// const text = ref('這是一段文字')
// const city = ref('高雄市')
// const isChecked = ref(true)
// const arrayCheckbox = ref([])
// const radioValue = ref('女')
</script>

<template>
  <div>
    <!-- 此為常見寫碼方式-->
    <h1>目連累加到的數字為 : {{ num }}</h1>
    <h1 v-text="num"></h1>
    {{ htmltemplate }}
    <div v-text="htmltemplate"></div>
    <!-- 此為這正確的方式，有套用到 h1 效果 -->
    <div v-html="htmltemplate"></div>

    <!-- <div>
      姓名: {{ array[0].name }} 年齡: {{ array[0].age }}
      <hr />
    </div>

    <div v-for="(item, key) in array" v-bind:key="item.id">
      索引: {{ key }} 姓名: {{ item.name }} 年齡: {{ item.age }}
      <div v-if="item.age > 18">大於18歲</div>
      <div v-else>小於18歲</div>
      <hr />
    </div>

    <hr />
    <input type="checkbox" v-model="isChecked" /> {{ isChecked }}

    <h1 v-if="isChecked">當 isChecked == true 會顯示這行</h1>
    <h1 v-else>目前的 isChecked 為 false</h1>
    <h1 v-show="isChecked">當 isChecked == true 會顯示這行 (與 if 不同，show 為隱藏此行文字)</h1> -->

    <!-- <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />

    <form action="" @submit.prevent="submitFrom">
      <button type="button" v-on:click="handleClick">點我</button>
      <button type="submit">點我</button>
    </form>

    <h2>事件修飾符</h2>
    <a href="#" @click.prevent="handleClick">點我</a>

    <h2>按鍵修飾符</h2>
    <input type="text" v-on:keydown.enter="handleClick" v-model="text" /> -->

    <!-- <h2>可以套用在任何屬性上</h2>
    <img v-bind:src="imgUrl" alt="" />
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
    <input type="text" v-bind:disabled="isChecked" />
    <h2>可以套用在行內樣式上</h2>
    <div class="box" v-bind:style="{ transform: isChecked ? 'rotate(45deg)' : null }"></div>
    <div class="box" v-bind:style="{ backgroundColor: isChecked ? 'aqua' : 'red' }"></div> -->

    <!-- <h2>class</h2> -->
    <!-- 需要套用的 className, 變數 -->
    <!-- <div class="box" v-bind:class="{ rotate: isChecked }"></div> -->

    <!-- 以下為 V-model 雙向綁定 -->
    <!-- <h1>{{ text }}</h1>
    <input type="text" v-model="text" /> -->
    <!-- 表單功能 -->
    <!-- {{ city }}
    <select name="" id="" v-model="city">
      <option value="高雄市">高雄市</option>
      <option value="台北市">123</option>
      <option value="台中市">456</option>
    </select> -->
    <!-- checkbox 1. true false, 方塊勾選 2. array value 存放陣列的值 -->
    <!-- <hr />
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
    <hr />
    {{ arrayCheckbox }}
    <input type="checkbox" v-model="arrayCheckbox" value="5566" />
    <input type="checkbox" v-model="arrayCheckbox" value="7788" />
    <input type="checkbox" v-model="arrayCheckbox" value="2266" />
    <input type="checkbox" v-model="arrayCheckbox" value="9527" /> -->

    <!-- radio 單一值 -->
    <!-- <hr />
    {{ radioValue }}
    <input type="radio" v-model="radioValue" value="男" />
    <input type="radio" v-model="radioValue" value="女" /> -->
  </div>
</template>

<style>
/* .box {
  height: 90px;
  width: 90px;
  background-color: aqua;
  transition: 1s all;
}
.rotate {
  transform: rotate(45deg);
} */
</style>
