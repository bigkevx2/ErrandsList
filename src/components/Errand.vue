<template>
    <div class="errand-line">
            <span class="errand-title">
            <input type="checkbox" v-on:change="$emit('in-basket', Errand.id)">
                {{Errand.count}} x {{Errand.errand}}
            </span>
            <span class="index-buttons">
                <button v-if="index!==0" @click="$emit('move-up', index)" class="button-up">Move up</button>
                <button @click="$emit('move-down', index)" class="button-down">Move down</button>
                <button @click="$emit('del-errand', Errand.id)" class="del">Delete</button>
            </span>
        <div class="index-buttons-small">
            <span>
                <button v-if="index!==0" @click="$emit('move-up', index)" class="button-up">Move up</button>
                <button @click="$emit('move-down', index)" class="button-down">Move down</button>
                <button @click="$emit('del-errand', Errand.id)" class="del">Delete</button>
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Errand",
        props: ["Errand", "index"]
    }
</script>

<style scoped>
    .index-buttons-small {
        /*visibility: hidden;*/
        display: none;
    }
    .errand-line {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .errand-title {
        /*margin-left: 30px;*/
    }

    .index-buttons {
        float: right;
    }

    button {
        margin-right: 10px;
        width: 60px;
        height: 20px;
    }

    button:hover {
        background: whitesmoke;
    }

    .del {
        background: #fb8d11;
        color: black;
        width: 60px;
    }
    .del:hover {
        background: #ff0000;
        color: #fff;
    }

    input {
        margin-left: 10px;
        margin-right: 10px;

    }

    @media only screen and (max-width: 768px){
        .index-buttons-small {
            display: block;
        }
        .index-buttons {
            display: none;
        }
        .errand-title {
            margin-left: 0px;
        }
    }
</style>