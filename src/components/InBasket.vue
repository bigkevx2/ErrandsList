<template>
    <div class="errand-line">
        <p>
            <span class="errand-title">{{Errand.title}}</span>
        </p>
    </div>
</template>

<script>
    export default {
        name: "InBasket",
        props: ["Errand"]
    }
</script>

<style scoped>
    .errand-line {
        text-decoration: line-through;
        background: #7e7e7e;
        color: #2f2f2f;
    }
    .errand-title {
        margin-left: 55px;
    }
</style>