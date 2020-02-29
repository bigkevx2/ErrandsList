<template>
    <div class="errand-line">
        <p>
            <span class="errand-title">
            <input type="checkbox" v-on:change="$emit('in-basket', Errand.id)">
                {{Errand.count}} x {{Errand.errand}}
            </span>
            <span class="index-buttons">
                <button v-if="index!==0" @click="$emit('move-up', index)">Move up</button></span>
            <span>
                <button @click="$emit('move-down', index)">Move down</button></span>
            <button @click="$emit('del-errand', Errand.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: "Errand",
        props: ["Errand", "index"]
    }
</script>

<style scoped>
    .errand-line {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .errand-title {
        margin-left: 30px;
        width: 400px;
    }

    .index-buttons {
        margin-left: 200px;
    }

    .in-basket {
        text-decoration: line-through;
        background: #7e7e7e;
        color: #4b4b4b;
    }

    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>