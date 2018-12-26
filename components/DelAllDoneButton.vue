<template>
    <input
            type="button"
            value="Удалить все"
            @click="delAllDone"
    />
</template>

<script>
    export default {
        props: ['todos'],
        methods: {
            delAllDone() {
                for ( let i=0; i<this.todos.length; i++) {
                    if (this.todos[i].maked) {
                        this.todos.splice(i,1);
                        i--;
                    }
                }
            }
        },
    }
</script>

<style scoped>

</style>