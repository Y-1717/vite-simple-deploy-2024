<script setup>
import { ref } from 'vue'

const num = ref(1)   
function clickMe() {
  num.value++
}

</script>

<template>
  <div>
    {{ num }}
    <button type="button" v-on:click="clickMe">click</button>
  </div>
</template>

