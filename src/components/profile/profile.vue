
<script setup>
import Avartar from "./avartar.vue"
import Card from "../Card.vue"
import TwitterLogo from "./small-logos/TwitterLogo.vue";
import GithubLogo from "./small-logos/GithubLogo.vue";
import BilibiliLogo from "./small-logos/BilibiliLogo.vue"
import ZhihuLogo from "./small-logos/ZhihuLogo.vue"
</script>

<template>
    <Card>
        <Avartar></Avartar>
        <div class="profile-name">Cedaros</div>
        <div class="logobar">
            <GithubLogo linkto="https://github.com/Ce-daros"></GithubLogo>
            <TwitterLogo linkto="https://twitter.com/Ce_daros"></TwitterLogo>
            <BilibiliLogo linkto="https://space.bilibili.com/3493090178369961"></BilibiliLogo>
            <ZhihuLogo linkto="https://www.zhihu.com/people/51-5-46-78"></ZhihuLogo>
        </div>

    </Card>

</template>

<style scoped>
.card-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 300px;
    justify-content: space-around;
    min-width: 200px;
    max-width: 300px;
    width: 100%;

}

.small-icons {
    opacity: 90%;
    transition: all ease 0.15s;
}

.small-icons:hover:not(.githublogo) {
    opacity: 100%;
    transform: scale(1.2);
    transition: all ease 0.15s;
}

.profile-name {
    font-size: larger;
    margin-top: 20px;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    text-align: center;
}

.logobar {
    display: flex;
    width: 70%;
    justify-content: space-evenly;

}
</style>
