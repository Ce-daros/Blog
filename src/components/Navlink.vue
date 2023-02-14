<script setup>
import { computed } from 'vue'
const props = defineProps({
    txt: String, key1: String
})
function Navit() {
    window.location.href = "./" + props.key1;
}
</script>

<template>
    <div class="navlink-box">
        <div class="logo-box">
            <img class="logo">
        </div>
        <div class="title-box">
            <div class="title" @click="Navit()">
                {{ txt }}
            </div>
        </div>
    </div>
</template>

<style scoped>
.navlink-box {
    display: flex;
    flex-direction: row;
}
</style>
