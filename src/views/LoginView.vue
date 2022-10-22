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
    </div>
    <div id="clock">
      <date-time></date-time>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import DateTime from "../components/header/DateTime.vue";
const username = ref("");
const password = ref("");
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
#clock {
  color: aliceblue;
  position: absolute;
  top: 70%;
  left: 15%;
  text-align: left;
  font-size: 15px;
  width: 125px;
  font-weight: bold;
}
</style>
