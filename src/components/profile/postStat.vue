
<script setup>
import Card from '../Card.vue';
import global from '../../global.vue';
import { reactive } from 'vue';
var xhr = new XMLHttpRequest;

var c = document.cookie;
if (c.includes("you_have_reach_there")) {
    xhr.open("GET", "http://cedaros.pythonanywhere.com/get_visitor", false)
}
else {
    xhr.open("GET", "http://cedaros.pythonanywhere.com/set_visitor", false)
    document.cookie = "visitorTag=you_have_reach_there; expires=Thu, 4 June 2023 12:00:00 GMT"
}


var visitor = reactive(0);
xhr.onreadystatechange = function () {
    if (xhr.readyState == 4 && xhr.status == 200) {
        visitor = xhr.responseText;
        this.$forceUpdate();
        console.log(xhr.responseText);
    }
}
xhr.send();
</script>
<template>
    <Card>
        <div class="stat">
            <div class="visitors">

                <div class="visitors-count">{{ visitor }}</div>&nbsp;
                <div class="visitors-title">👀</div>

            </div>
            <div class="postsintotal">

                <div class="posts-count">{{ global.jsonOrg.lastestArtical.length }}</div>&nbsp;
                <div class="posts-title">📝</div>
            </div>
        </div>
    </Card>

</template>
<style scoped>
.stat,
.visitors,
.postsintotal,
.stat {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-evenly;
}

.card-container {
    padding-bottom: 20px;
}

.visitors,
.postsintotal {
    align-items: flex-end !important;
}
</style>