<script setup>
import Card from '../Card.vue';
import global from '../../global.vue'
import { ref } from 'vue';
var arts = ref(global.jsonData.lastestArtical);
var cats = ref(global.jsonData.categoryDefinitions);
var cai = ref(global.jsonData.categoryIndex);

function refreshData() {
    arts = ref(global.jsonData.lastestArtical);
    cats = ref(global.jsonData.categoryDefinitions);
    cai = ref(global.jsonData.categoryIndex);
}
function withTag(t) {
    global.jsonData.lastestArtical = global.jsonOrg.lastestArtical;
    if (t == "All") {
        refreshData();
        return;
    }
    var tempart = [];
    var j = 0;
    for (var i of global.jsonData.lastestArtical) {
        if (i.title.includes(t) || i.desc.includes(t)) {
            i.count = j;
            tempart.push(i);
            j++;
        }
    }
    global.jsonData.lastestArtical = tempart;
    refreshData();
}
function keypressHandler(e, o) {
    var e = event || window.event;
    if (e.key == "Enter") {
        e.preventDefault();
        withTag(e.srcElement.innerText);
    }
}
</script>
<template>
    <Card>
        <div class="searchbox-con" contenteditable="true" @keypress="keypressHandler(e); $emit('refreshed');"></div>
    </Card>
</template>
<style scoped>
.card-container {
    padding-top: 10px;
    padding-bottom: 10px;
    border-radius: 15px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.searchbox-con {
    background-color: var(--theme-dark-l);
    height: 35px;
    border-radius: 10px;
    width: 85%;
    line-height: 35px;
    border: none;
    padding-left: 5px;
    padding-right: 5px;
    font-size: smaller;
    overflow: hidden;
}

.searchbox-con:focus {
    border: none !important;
    outline: none !important;
}

.searchbox-con:focus::after {
    animation: searchBoxAni 1s ease;
    animation-fill-mode: forwards;
}

@keyframes searchBoxAni {


    0% {
        content: '🔍';
        opacity: 0.5;
    }

    45% {
        content: '🔍';
        opacity: 0;
    }

    55% {
        content: 'Press Enter';
        opacity: 0;
    }

    100% {
        content: 'Press Enter';
        opacity: 1;
    }
}

@keyframes searchBoxAniOut {


    0% {
        content: 'Press Enter';
        opacity: 1;
    }

    45% {
        content: 'Press Enter';
        opacity: 0;
    }

    55% {
        content: '🔍';
        opacity: 0;
    }

    100% {
        content: '🔍';
        opacity: 0.5;
    }

}

.searchbox-con::after {
    content: '🔍';
    float: right;
    opacity: 0.5;
    padding-left: 3px;
    animation: searchBoxAniOut 1s ease;
    animation-fill-mode: forwards;
}
</style>