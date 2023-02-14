<script setup>
import { ref } from 'vue';
import Card from '../Card.vue';
import Tagbox from './tagbox.vue';
import global from '../../global.vue'
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
        if (i.tags.includes(t)) {
            i.count = j;
            tempart.push(i);
            j++;
        }
    }
    global.jsonData.lastestArtical = tempart;
    refreshData();
}
</script>
<template>
    <Card>
        <div class=" tagcard-container">
            <Tagbox :backcolor=i.color :desc="i.name" :namekey="i.name" @click="withTag(i.name); $emit('refreshed');"
                v-for="i in cats">
                <img style="width: 15px;height:15px;" :src="'src/' + i.icon">
            </Tagbox>
            
        </div>
    </Card>
</template>
<style scoped>
.card-container {
    display: flex;
    justify-content: center;
}

.tagcard-container {
    display: flex;
    flex-direction: row;
    width: 90%;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-evenly;
}

.das {
    border: 2px solid white;
}
</style>