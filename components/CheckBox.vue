<template>
    <div>
        <input type="checkbox" v-model="todos.maked"/>
        <item-name-box :todos="todos" :choosed="choosed" @choosed="$emit('choosed', todos.id)"
                       @changed="$emit('changed', [$event, index])" @canceled="$emit('canceled')"/>
        <input type="button" value="x" @click="$emit('del')"/>
    </div>
</template>

<script>
    // @todo: название компонента сменить (вводит в заблуждение)
    import ItemNameBox from "./ItemNameBox.vue"

    export default {
        components: {
            ItemNameBox,
        },
        // @todo: todos - во множественном числе, должно быть в единственном и более точное название
        props: ["todos", "choosed", "index"],
    }
</script>
