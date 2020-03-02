<template>
    <div>
        <div v-bind:key="Errand.id" v-for="(Errand,index) in Errands">
            <Errand v-bind:Errand="Errand"
                    v-bind:index="index"
                    v-bind:arraySize="arraySize=Errands.length"
                    v-on:del-errand="$emit('del-errand', Errand.id)"
                    v-on:in-basket="$emit('in-basket', Errand.id)"
                    v-on:move-up="$emit('move-up', index)"
                    v-on:move-down="$emit('move-down', index)"
            />
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