<template>
    <div class="topbar">
        <div class="navcard-navbar">
            <Card>
                <div class="navcard-bar">
                    <div class="navcard-link">
                        🏠
                    </div>
                    <div class="navcard-link">
                        🧾
                    </div>
                    <div class="navcard-link">
                        ❓
                    </div>
                </div>
            </Card>
        </div>
        <div class="udttime">
            <Card>
                <div class="navcard-time">
                    <center>更新✅ 2023-02-15</center>
                </div>
            </Card>
        </div>
    </div>
</template>
<script setup>
import Card from '../Card.vue';
</script>
<style scoped>
@media screen and (orientation:landscape) {
    .topbar {
        display: flex;
        width: 350px;
        margin-left: 25%;
        flex-direction: row;
        align-items: center;
        justify-content: space-evenly;
    }

    .navcard-time {
        font-size: medium;
    }

    .udttime {
        width: 160px;
        height: 45px;
        margin-bottom: 10px;
        display: flex;
        line-height: 20px;
        align-items: center;
        justify-content: center;
    }

    .card-container {
        margin-bottom: 5px;
        padding-top: 10px;
        padding-bottom: 10px;
    }


    .navcard-navbar {
        width: 160px;
        height: 45px;
        margin-bottom: 10px;
        display: flex;
        line-height: 20px;
        align-items: center;
        justify-content: center;
    }

    .navcard-bar {
        display: flex;
        align-items: center;
        justify-content: space-evenly;

    }

    .navcard-link {
        font-size: large;
    }
}

@media screen and (orientation:portrait) {
    .topbar {
        display: flex;
        width: 350px;
        flex-direction: row;
        align-items: center;
        justify-content: space-evenly;
    }

    .navcard-time {
        font-size: medium;
    }

    .udttime {
        width: 160px;
        height: 45px;
        margin-bottom: 10px;
        display: flex;
        line-height: 20px;
        align-items: center;
        justify-content: center;
    }

    .card-container {
        margin-bottom: 5px;
        padding-top: 10px;
        padding-bottom: 10px;
    }


    .navcard-navbar {
        width: 160px;
        height: 45px;
        margin-bottom: 10px;
        display: flex;
        line-height: 20px;
        align-items: center;
        justify-content: center;
    }

    .navcard-bar {
        display: flex;
        align-items: center;
        justify-content: space-evenly;

    }

    .navcard-link {
        font-size: large;
    }
}
</style>