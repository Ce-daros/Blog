<script setup>

const props = defineProps({
    backcolor: String, desc: String, namekey: String, a: String
})
</script>
<template>
    <div class="tagbox-con" :style="{ backgroundColor: backcolor }">
        <div class="tagicon">
            <slot></slot>
        </div>
        <div class="tagdesc">
            {{ desc }}
        </div>
    </div>
</template>
<style scoped>
.tagbox-con {
    background-color: var(--theme-dark-l);
    border-radius: 5px;

    margin: 2px;
    margin-bottom: 8px;
    padding: 4px;
    padding-bottom: 2px;
    display: flex;
    align-items: center;
    transition: all ease 0.2s;
    box-shadow: 0px 2px 5px 0px rgba(0, 0, 0, 0.14),
        0px 1px 10px 0px rgba(0, 0, 0, 0.12),
        0px 2px 4px -1px rgba(0, 0, 0, 0.2);

}

.tagicon {
    transform: translateY(2px);
}

.tagbox-con:hover {
    transform: scale(1.1);
    box-shadow: 0px 8px 17px 2px rgba(0, 0, 0, 0.14),
        0px 3px 14px 2px rgba(0, 0, 0, 0.12),
        0px 5px 5px -3px rgba(0, 0, 0, 0.2);
    transition: all ease 0.2s;
}

.tagdesc {
    margin-left: 2px;
    font-size: 1px;
}
</style>