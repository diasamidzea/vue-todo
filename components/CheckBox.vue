<template>
    <div>

        <input
                type="checkbox"
                v-model="todos.maked"
        />
        <item-name-box
                :todos="todos"
                :choosed="choosed"
                @choosed="$emit('choosed', todos.id)"
                @changed="$emit('changed')"
        ></item-name-box>
        <input
                type="button"
                value="x"
                @click="$emit('del')"
        />

    </div>
</template>

<script>
    import ItemNameBox from "./ItemNameBox.vue"

    export default {
        components: {
            ItemNameBox,
        },
        props: ['todos', 'choosed'],
    }
</script>

<style scoped>

</style>