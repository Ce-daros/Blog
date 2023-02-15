<script setup>
import Profile from "./components/profile/profile.vue";
import Tagcard from './components/tagcard/tagcard.vue';
import Articalcard from './components/articlecard/articalcard.vue';
import global from './global.vue';
import navcard from "./components/Navcard/navcard.vue";
import searchBox from './components/searchBox/searchBox.vue';
import postStat from "./components/profile/postStat.vue";
import { ref } from 'vue';
var arts = ref(global.jsonData.lastestArtical);
function rit() {
  arts = ref(global.jsonData.lastestArtical);
}
</script>

<template>
  <NavbarTop></NavbarTop>
  <div class="second_screen">
    <div class="left-bar">
      <Profile></Profile>
      <searchBox @refreshed="rit(); $forceUpdate();"></searchBox>
      <Tagcard @refreshed="rit(); $forceUpdate();"></Tagcard>
      <postStat></postStat>
    </div>
    <div class="right-bar">
      <navcard></navcard>
      <div class="subtitle">Recent Posts</div>
      <Articalcard :readtime=i.timeToRead :wrotenTime=i.time :artlen=i.len :arttitle=i.title :artdesc=i.desc
        :count=i.count :wrotentime=i.time :arttxt=i.text v-for="i in global.jsonData.lastestArtical"></Articalcard>

    </div>
  </div>
</template>

<style scoped>
.subtitle {
  font-size: x-large;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  margin-top: 10px;
  margin-bottom: 10px;
}

@media screen and (orientation:landscape) {
  .first_screen {
    height: 95vh;
  }

  .left-bar {
    display: flex;
    flex-direction: column;
    width: 26%;
    align-items: center;
    max-width: 300px;
    min-width: 200px;
    margin-right: 10px;
  }

  .right-bar {
    display: flex;
    flex-direction: column;
    width: 65%;
    margin-left: 10px;
  }

  .second_screen {
    padding-left: 100px;
    padding-top: 5vh;
    padding-bottom: 5vh;
    padding-right: 100px;
    height: 90vh;
    background-color: var(--theme-dark-b);
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }

}

@media screen and (orientation:portrait) {
  .first_screen {
    height: 95vh;
  }

  .left-bar {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
    max-width: 400px;
    min-width: 200px;
  }

  .right-bar {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
  }

  .second_screen {
    padding-left: 20px;
    padding-top: 2vh;
    padding-bottom: 5vh;
    padding-right: 20px;
    height: 90vh;
    background-color: var(--theme-dark-b);
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
