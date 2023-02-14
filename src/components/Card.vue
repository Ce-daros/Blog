
<template>
    <div class="card-container">
        <slot></slot>
    </div>
</template>

<style scoped>
@media screen and (orientation:landscape) {
    .card-container {
        background-color: var(--theme-dark);
        border-radius: 15px;
        padding: 15px;
        padding-left: 0;
        padding-right: 0;
        width: 100%;
        margin-bottom: 30px;
        color: var(--theme-light);
        transition: all ease-in-out 0.3s;
        box-shadow: 0px 0px 0px 1px rgba(255, 255, 255, 0.2);
    }
}

@media screen and (orientation:portrait) {
    .card-container {
        background-color: var(--theme-dark);
        border-radius: 15px;
        padding: 15px;
        padding-left: 0;
        padding-right: 0;
        width: 100%;
        padding-top: 20px;
        margin-bottom: 20px;
        color: var(--theme-light);
        transition: all ease-in-out 0.3s;
        box-shadow: 0px 0px 0px 1px rgba(255, 255, 255, 0.2);
    }
}
</style>
