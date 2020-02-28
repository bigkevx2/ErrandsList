<template>
    <div>
        <div v-bind:key="Errand.id" v-for="Errand in Errands">
            <Errand v-bind:Errand="Errand"
                      v-on:del-errand="$emit('del-errand', Errand.id)"/>
        </div>
    </div>
</template>

<script>
    import Errand from "@/components/Errand";
    export default {
        name: "ErrandList",
        props: ["Errands"],
        components: {
            Errand
        }
    }
</script>

<style scoped>

</style>