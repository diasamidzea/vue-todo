<template>
    <div style="display: inline">
        <span @click="$emit('choosed')" v-if="(todos.id !== choosed)">
            {{ todos.name }}
        </span>
        <form v-if="(todos.id === choosed)" @submit.prevent="ChangeName" style="display: inline">
            <input v-model="newName"/>
            <input type="submit" value="ok"/>
            <input type="button" @click="$emit('canceled'); newName = todos.name" value="cancel"/>
        </form>
    </div>
</template>

<script>
    // todo: стиили из шаблона вынести в <style>
    export default {
        // @todo
        props: ["todos", "choosed"],
        data() {
            return {
                newName: this.todos.name,
            }
        },
        methods: {
            // @todo
            ChangeName() {
                this.$emit("changed", this.newName)
            }

        }
    }
</script>