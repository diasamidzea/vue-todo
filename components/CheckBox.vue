<template>
    <div>
        <input type="checkbox" v-model="todos.maked"  />
        <item-name-box :todos="todos" :choosed="choosed" @choosed="$emit('choosed', todos.id)"
                       @changed="$emit('changed', [$event, index])" @canсeled="$emit('canсeled')" />
        <input type="button" value="x" @click="$emit('del')"  />
    </div>
</template>

<script>
    import ItemNameBox from "./ItemNameBox.vue"

    export default {
        components: {
            ItemNameBox,
        },
        props: ['todos', 'choosed', 'index'],
    }
</script>

<style scoped>

</style>