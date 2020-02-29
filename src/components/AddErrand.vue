<template>
    <div>
        <form @submit="addErrand">
            <input type="text" v-model="count" name="count" placeholder="count">
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
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
        height: 50px;
        font-size: 25px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>