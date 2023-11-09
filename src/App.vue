<script setup>
import { ref } from "vue";
const showmodal = ref(false);
const text = ref("");
const error_text = ref("");
// const open = () => {
//   showmodal.value = true;
// }
let obj = [];
const addnote = () => {
  if (text.value.length > 3) {
    const data = {
      id: Math.floor(Math.random() * 20000),
      text: text.value,
      colorBg: `hsl(${Math.random() * 360}, 90%, 80%)`
    }
    showmodal.value = false;
    error_text.value = "";
    text.value = "";
    obj.push(data);
  } else {
    error_text.value = "Please Character length greater than 3 needed !";
  }
}
</script>
<template>
  <div class="top_of" v-if="showmodal">
    <div class="inputs">
      <textarea name="" id="" cols="30" rows="10" v-model="text"></textarea>
      <p style="color:red; font-size:small; tex-align:center">{{ error_text }}</p>
      <button class="add" @click="addnote()">Add Note</button>
      <button class="cancel" @click="showmodal = false">Cancel</button>
    </div>
  </div>
  <main>
    <div class="banner">
      <div>
        <h3 class="title">NOTE BOOK</h3>
        <!-- <p>{{ text }}</p> -->
      </div>
      <div>
        <button class="addn" @click="showmodal = true">Add Note</button>
      </div>
    </div>
    <div class="content">
      <div class="card" v-for="object in obj" key="object.id" :style="{ backgroundColor: object.colorBg }">
        <span>{{ object.text }}</span>
        <div class="date"><span>{{ (new Date()).toLocaleDateString("en-US") }}</span></div>
      </div>

    </div>
  </main>
</template>
<style scoped>
body {
  overflow: hidden;
}

main {
  margin-left: calc(100vw - 90vw);
  margin-right: calc(100vw - 90vw);
}

.content {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
  align-items: center;
}

.card {
  width: 250px;
  background-color: royalblue;
  border-radius: 10px;
  color: black;
  padding: 10px;
  font-size: 12px;
}

.date {
  font-size: small;
  color: rgb(30, 46, 36);
  margin-top: 30px;
}

.title {
  font-weight: 500;
  font-size: 30px;
}

.addn {
  padding: 10px;
  border-radius: 10px;
  background-color: hsl(145, 94%, 31%);
  color: white;
  border: none;
}

.banner {
  display: flex;
  width: 100%;
  position: relative;
}

.banner>* {
  margin: 10px;
  width: 100%;
}

.banner>*:nth-child(2) {
  text-align: end;
  margin-top: 10px;
}

.top_of {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.342);
  z-index: 2;
  backdrop-filter: blur(10px);
}

.inputs {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 10px;
  border-radius: 10px;
  width: 400px;
  background-color: white;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.384);
}

.inputs>textarea {
  background: none;
  resize: none;
  width: 100%;
  border-radius: 10px;
  border: none;
  box-shadow: inset 0px 0px 10px 0px rgba(0, 0, 0, 0.308);
  display: grid;
}

.inputs button {
  padding: 10px;
  width: 95%;
  background-color: rgb(0, 122, 75);
  color: white;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  border-radius: 10px;
  border: none;
  margin: 10px;
  outline: none;
}

.inputs button {
  padding: 10px;
  width: 95%;
  background-color: rgb(0, 0, 0);
  color: rgb(255, 255, 255);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  border-radius: 10px;
  border: none;
  margin: 10px;
  outline: none;
}

.inputs button:nth-child(3) {
  background-color: red;
}
</style>
