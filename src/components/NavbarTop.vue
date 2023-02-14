<script setup>
import { ref } from 'vue'
import Navlink from './Navlink.vue'
defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <div class="nav-bar">
    <div class="logo-box">
      <div class="logo">

      </div>
    </div>
    <div class="nav-links">
      <Navlink txt="" key1="1.html"></Navlink>
    </div>
  </div>
</template>

<style scoped>
.nav-bar {
  display: flex;
  flex-direction: row;
  opacity: 90%;
  height: 5vh;
  color: var(--theme-light);
  padding-right: 20px;
  padding-left: 20px;

}

.logo-box {
  display: flex;
  align-items: center;
}

.nav-links {
  display: flex;
  flex-grow: 1;
  height: 100%;
  align-items: center;
  flex-direction: row;
  justify-content: flex-end;

}
</style>
