<template>
    <div class="errand-line">
        <p>
            <span class="errand-title">{{Errand.count}} x {{Errand.errand}}</span>
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

    @media only screen and (max-width: 768px){
        .errand-title {
            margin-left: 30px;
        }
    }
</style>