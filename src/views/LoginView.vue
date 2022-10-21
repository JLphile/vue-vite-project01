<template>
  <div id="background">
    <div id="logo">mySystem</div>
    <div id="login">
      <el-card class="box-card">
        <div id="form">
          <el-input v-model="username" placeholder="Please input" />
          <el-input
            v-model="password"
            type="password"
            placeholder="Please input password"
            show-password
          />
          <el-button type="primary">登陆</el-button>
        </div>
      </el-card>
      <div id="clock">
        <div id="time">{{ time }}</div>
        <div id="date">{{ date }}</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const username = ref("");
const password = ref("");

const d = new Date();
let year: string | number = d.getFullYear();
let mon: string | number = d.getMonth() + 1;
let day: string | number = d.getDate();
let hour: string | number = d.getHours();
let min: string | number = d.getMinutes();
if (year < 10) {
  year = "0" + String(year);
}
if (year < 10) {
  year = "0" + String(year);
}
if (mon < 10) {
  mon = "0" + String(mon);
}
if (day < 10) {
  day = "0" + String(day);
}
if (hour < 10) {
  hour = "0" + String(hour);
}
if (min < 10) {
  min = "0" + String(min);
}
let date = year + "/" + mon + "/" + day;
let time = hour + ":" + min;
</script>

<style scoped>
#background {
  position: fixed;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  background-image: linear-gradient(90deg, cyan, purple);
  background-size: 400%;
  animation: myanimation 10s infinite;
}
@keyframes myanimation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
#logo {
  color: aliceblue;
  font-size: 25px;
  font-weight: 800;
  text-transform: uppercase;
  position: absolute;
  top: 15%;
  left: 15%;
}
#login {
  position: absolute;
  top: 30%;
  left: 38%;
}
#form {
  line-height: 60px;
  padding-left: 15px;
  padding-right: 15px;
}

.box-card {
  width: 373px;
  height: 210px;
  background-color: rgba(255, 255, 255, 0.3);
  border-radius: 15px;
}
</style>
