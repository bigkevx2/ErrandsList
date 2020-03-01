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
        display: none;
    }
    .errand-line {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .index-buttons {
        float: right;
    }

    button {
        margin-right: 10px;
        width: 75px;
        height: 20px;
        background: #555;
        color: #fff
    }

    button:hover {
        background: #666;
    }

    .del {
        background: #fdc414;
        color: black;
        width: 75px;
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

        button {
            width: 45%;
            height: 30px;
        }

        .del {
            width: 93%;
        }
    }
</style>