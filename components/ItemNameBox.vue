<template>
    <div style="display: inline">
        <span
                @click="$emit('choosed')"
                v-if="(todos.id !== choosed)"
        >{{ todos.name }}
        </span>

        <form
                v-if="(todos.id === choosed)"
                @submit.prevent = "$emit('changed')"
                v-model="newName"
                style="display: inline"
        >
            <input v-model="newName"/>
        </form>
    </div>
</template>

<script>
    export default {
        props: ['todos', 'choosed'],
        data() {
            return {
                newName: this.todos.name,
                //isMarkedForChange: false
            }
        },
        /*methods: {
            MarkedForChange () {
                this.isMarkedForChange=true;
            }

        }*/
    }
    //console.log(this.marked);
</script>

<style scoped>

</style>