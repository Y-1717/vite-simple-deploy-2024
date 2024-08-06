<script setup>
  import { ref } from 'vue'

  const num = ref(1)
  const text = ref('這是一段文字')
  const city = ref('台北')
  const isChecked = ref(true)
  const arrayCheckbox = ref([])
  const radioValue = ref('男')
  const imgUrl = ref('https://plus.unsplash.com/premium_photo-1721579535060-1cb020f041c2?q=80&w=400&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')
  const array = ref([
    {
      id: 1,
      name: '小名',
      age: 18
    }, {
      id: 2,
      name: '小黑',
      age: 13  
    }, {
      id: 3,
      name: '阿依',
      age: 33  
    }
  ])

  function clickMe() {
    num.value++
  }

  function handleClick() {
    console.log('我被觸發了')
  }

  function submitForm() {
    console.log('表單觸發了')
  }
</script>

<template>
  <div>
    {{ num }}
    <button type="button" v-on:click="clickMe">click</button>
  </div>
  <hr />
  <div>
    <h3> {{ text }} </h3>
    <input type="text" v-model="text" />
  </div>
  <hr />
  <!-- 表單 -->
  <div> {{ city }}
    <select id="" name="" v-model="city">
      <option value="台北">台北</option>
      <option value="台南">2222</option>
      <option value="高雄">高雄</option>
    </select>
  </div>
  <hr />
  <!-- checkbox 1. true false, 2. array value -->
  <div> {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
  </div>
  <hr />
  <div> {{ arrayCheckbox }}
    <input type="checkbox" v-model="arrayCheckbox" value="小美" />
    <input type="checkbox" v-model="arrayCheckbox" value="小名" />
    <input type="checkbox" v-model="arrayCheckbox" value="小黑" />
  </div>
  <hr />
  <!-- radio 單一值 -->
  <div> {{ radioValue }}
  <input type="radio" v-model="radioValue" value="男" />    
  <input type="radio" v-model="radioValue" value="女" />    
  </div> 
  <hr />
  <!-- v-bind -->
  <div>
    <img :src="imgUrl" alt="" />
  </div>
  <hr />
  <div>
    <h2>可以套用在任何的屬性上</h2>
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
    <!-- <input type="text" v-bind:disabled="isChecked" /> -->
    <input type="text" :disabled="isChecked" />
  </div>
  <div>
    <h2>可以套用在行內樣式上</h2>
    <div class="box" :style="{ transform: isChecked ? 'rotate(45deg)' : null }"></div>
    <div class="box" :style="{ backgroundColor: isChecked ? 'red' : 'green' }"></div>
  </div>
   <div>
    <h2>Class</h2>
    <!-- 需要套用的 className, 變數 -->
    <div class="box" :class="{ rotate: isChecked }"></div>
  </div>
  <hr />
  <div>
    <form action="" @submit.prevent="submitForm">
      <button type="button" v-on:click="handleClick">點我</button>
    </form>
    <h2>事件修飾符</h2>
    <a href="#" @click.prevent="handleClick">點我</a>
    <h2>按鍵修飾符</h2>
    <input type="text" @keydown.enter="handleClick"/>
  </div>
  <hr />
  <div>
    <div v-for="(item, index) in array" :key="item.id">
      索引: {{ index}}
      姓名: {{ item.name }}
      年齡: {{ item.age }}
      <p v-if="item.age > 18">大於 18 歲</p>
      <p v-else-if="item.age == 18">等於 18 歲</p>
      <p v-else>小於 18 歲</p>
      <br />
    </div>
  </div>
  <hr />
  <div>
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
    <h2 v-if="isChecked">當 isChecked == true 時顯示</h2>
    <h2 v-else>目前的 isChecked 為 false</h2>
    <h2 v-show="isChecked">true/false 只是有沒有 display: none 的差別</h2>
  </div>

</template>

<style>
  div {
    width: 600px;
    margin: 20px auto;
  }
  
  .box {
    height: 100px;
    width: 100px;
    background-color: red;
    transition: .5s all;
  }

  .rotate {
    transform: rotate(45deg);
  }
</style>
