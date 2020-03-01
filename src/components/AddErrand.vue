<template>
    <div class="wide">
        <form @submit="addErrand">
            <input type="number" min="1" v-model="count" name="count" placeholder="Quantity">
            <input type="text" v-model="errand" name="title" placeholder="Errand...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
    export default {
        name: "AddErrand",
        data() {
            return {
                errand: '',
                count: ''
            }
        },
        methods: {
            addErrand(e) {
                e.preventDefault();
                const newErrand = {
                    id: Math.round(Math.random() * 1000),
                    count: this.count,
                    errand: this.errand,
                    completed: false
                };
                this.count='';
                this.errand='';
                this.$emit('add-errand', newErrand);
            }
        }
    }
</script>

<style scoped>
    form {
        display: block;
    }

    ::placeholder {
        color: lightgrey;
    }
    input[type="number"] {
        padding: 5px;
        height: 50px;
        font-size: 25px;
        width: 33%;

    }

    input[type="text"] {
        padding: 5px;
        height: 50px;
        font-size: 25px;
        width: 33%;
    }

    input[type="submit"] {
        padding: 5px;
        height: 50px;
        font-size: 25px;
        width: 33%;
    }

    @media only screen and (max-width: 768px){
        input[type="text"] {
            width: 360px;
        }
        input[type="submit"] {
            width: 360px;
        }
    }
</style>