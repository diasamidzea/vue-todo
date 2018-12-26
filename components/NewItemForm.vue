<template>
    <div>
        <form @submit.prevent="newtodo">
            <input
                    v-model="newTodoName"
                    placeholder="Введите задание"
            >
            <input type="submit" value="+" />
        </form>
    </div>
</template>

<script>
    export default {
        props: [ "todolist" ],
        data() {
            return {
                newTodoName: ""
            }
        },
        methods: {
            newtodo() {
                if (this.newTodoName) {
                    this.todolist.push({
                        id: (this.todolist[this.todolist.length-1].id+1),
                        maked: false,
                        name: this.newTodoName
                    });
                    this.newTodoName = "";
                };
            }
        }
    }
</script>

<style scoped>

</style>