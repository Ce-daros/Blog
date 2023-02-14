<script setup>
import Penicon from './tinylogo/penicon.vue';
import Clockicon from './tinylogo/clockicon.vue';
import Bookicon from './tinylogo/bookicon.vue';
import Tagbox from '../tagcard/tagbox.vue';
import Card from '../Card.vue';
import hljs from "highlight.js";
import global from '../../global.vue'
import { ref, Transition } from 'vue';
var arts = ref(global.jsonData.lastestArtical);
var cats = ref(global.jsonData.categoryDefinitions)
var cai = ref(global.jsonData.categoryIndex)
var a = ref(false)
const props = defineProps({
    wrotentime: String, arttitle: String, artdesc: String, count: Number, arttxt: String, b: String
})
function toLength(l) {
    if (l > 999) {
        return (l / 1000).toFixed(1) + "k";
    } else {
        return String(l);
    }
}
setTimeout(hljs.highlightAll, 100)
function toSpeed(l) {
    var s = l / 500 * 60;
    if (s > 59) {
        return (s / 60).toFixed(1) + " min";
    } else {
        return "~1 min";
    }
}
function switchA(t) {
    if (a.value == t) a.value = !t;


    var ev = window.event || arguments.callee.caller.arguments[0];
    if (window.event) ev.cancelBubble = true;
    else {
        ev.stopPropagation();
    }
}
console.log(props.count);
var l = global.jsonData.lastestArtical[props.count].text.length;
var artlen = ref(toLength(l));
var readtime = ref(toSpeed(l))
</script>
<template>

    <Card>
        <Transition name="artcon">
            <div class="artical-con" @click="switchA(false);">
                <div class="artical-meta">
                    <div class="artical-meta-con">
                        {{ b }}
                        <div class="artical-meta-wrotentime">
                            <Clockicon></Clockicon>
                            {{ wrotentime }}
                        </div>
                        <div class="artical-meta-length">
                            <Penicon></Penicon>
                            {{ artlen }}
                        </div>
                        <div class="artical-meta-timetoread">
                            <Bookicon></Bookicon>
                            {{ readtime }}
                        </div>

                    </div>
                    <div class="artical-tags">
                        <Tagbox :backcolor="cats[cai.indexOf(i)].color" :desc="i" v-for="i in arts[count].tags">
                            <img style="width: 15px;height:15px;transform: translateY(-1px);"
                                :src="'src/' + cats[cai.indexOf(i)].icon">
                        </Tagbox>

                    </div>
                    <Transition name="artcloseicon">
                        <div class="artical-close-button" v-if=a @click="switchA(true);">
                            <img class="artical-close-icon" src="../../assets/close.png">
                        </div>
                    </Transition>
                </div>
                <div class="artical-titlebar">
                    <div class="artical-title">
                        {{ arttitle }}
                    </div>
                </div>
                <div class="artical-desc-container">
                    <div class="artical-desc">
                        {{ artdesc }}
                    </div>
                    <Transition name="arttxt">
                        <div class="artical-txt" :class="{ show: !a }">

                            <div class="artical-txt" :class="{ show: !a }" v-html=arttxt></div>
                        </div>
                    </Transition>
                </div>

            </div>
        </Transition>
    </Card>

</template>
<style scoped>
.artical-con {
    padding: 15px;
    padding-top: 0px;
    padding-left: 40px;
    padding-right: 40px;
    transition: all ease-in-out 0.3s;
}

.show {
    display: none;
    opacity: 0;
}

.artical-meta {
    font-size: xx-small;
    display: flex;
    flex-direction: row;
    align-items: center;
    margin-bottom: 10px;
}

.artical-close-icon {
    width: 20px;
    height: 20px;
    margin-left: -20px;
    transform: translateY(-2px) translateX(20px);
}

.arttxt {
    display: block;
    opacity: 1;
    transition: all ease 0.2s;
}

.arttxt-enter-active,
.arttxt-leave-active {
    transition: opacity 0.5s ease;
}

.arttxt-enter-from,
.arttxt-leave-to {
    opacity: 0;
}

.artcloseicon-enter-active,
.artcloseicon-leave-active {
    transition: all 0.5s ease;
}

.artcloseicon-enter-from,
.artcloseicon-leave-to {
    opacity: 0;
    transform: scale(0.5);
}


.artical-titlebar {
    margin-bottom: 5px;
}

.artical-tags {
    display: flex;
    flex-grow: 1;
    flex-direction: row-reverse;
    padding-right: 10px;
}

.artical-txt {
    font-size: xx-small;
    margin-top: 30px;
}

.artical-meta-con {
    display: flex;
    flex-direction: row;
    align-items: center;
    width: 55%;

}

.art-icons {
    margin-right: 4px;
}

.artical-title {
    font-size: xx-large;
    font-family: 华文中宋, 宋体,
        SimSun,
        华文细黑,
        STXihei,
        sans-serif;
}


.artical-meta-timetoread {
    display: flex;
    align-items: center;
}

.artical-meta-length {
    display: flex;
    align-items: center;
    margin-right: 20px;
}

.artical-meta-wrotentime {
    display: flex;
    align-items: center;
    margin-right: 20px;
}
</style>