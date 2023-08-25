<script setup>
import { ref } from 'vue'
import { reactive } from 'vue';

defineProps({
  msg: String,
})

const count = ref(0)
let name = ref('Preeyanuch')
const lightStatus= ref(false)
function turnOn() {
lightStatus = !lightStatus.value;


 const styleObject = reactive({
  color: "Pink",
  fontSize: "50px",
 });
 function upsize(){
  count.value++

  //"50px" >> "50"  ลบ px
  console.log(styleObject.fontSize.slice(0,-2))

  //"50" >> 50 str to int
  let fsize=
  parseInt(styleObject.fontSize.slice(0,-2))
  styleObject.fontSize = fsize +count.value +"px"
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <h2 :style="styleObject">{{ name }}</h2>

<form>
  ชื่อ <input type="text" id="Fname" name="Fname" v-model="name">s
</form>

  <div class="card">
    <button @click="turnOn()">On/Off</button> {{ lightStatus.value }}
    <button type="button" @click="upsize()">Increase Font Size</button>
    <button type="button" @click="count++">count is {{ count }}</button>
  </div>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a>, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
.card {
  display: flex;
  align-items: center;
}
</style>
