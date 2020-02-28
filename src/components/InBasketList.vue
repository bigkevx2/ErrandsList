<template>
    <div>
        <div v-bind:key="Errand.id" v-for="Errand in InBasket">
            <InBasket v-bind:Errand="Errand"/>
        </div>
    </div>
</template>

<script>
    import InBasket from "@/components/InBasket";
    export default {
        name: "InBasketList",
        props: ["InBasket"],
        components: {
            InBasket
        }
    }
</script>

<style scoped>

</style>