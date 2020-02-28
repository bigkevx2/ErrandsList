<template>
    <div class="errand-line" v-bind:class="{'in-basket':Errand.completed}">
        <p>
            <input type="checkbox" v-on:change="inBasket">
            <span class="errand-title">{{Errand.title}}</span>
            <button @click="$emit('del-errand', Errand.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: "Errand",
        props: ["Errand"],
        methods: {
            inBasket() {
                this.Errand.completed = !this.Errand.completed;
            }
        }
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