<template>
    <div style="display: inline">
        <span @click="$emit('choosed')" v-if="(todos.id !== choosed)">
            {{ todos.name }}
        </span>
        <form v-if="(todos.id === choosed)" @submit.prevent="ChangeName" style="display: inline">
            <input v-model="newName"  />
            <input type="submit" value="ok"  />
            <input type="button" @click="$emit('canсeled'); newName = todos.name" value="cansel" />
        </form>
    </div>
</template>

<script>
    export default {
        props: ['todos', 'choosed'],
        data() {
            return {
                newName: this.todos.name,
            }
        },
        methods: {
            ChangeName () {
                this.$emit('changed',this.newName);
            }

        }
    }
</script>