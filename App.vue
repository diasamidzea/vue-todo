<template>
    <div>
        <new-item-form :todolist="todoList"></new-item-form>
        <h3>Не выполнено</h3>
        <div v-for="(todo, index) in todoList" :key="todo.id">
            <check-box
                    v-if="!todo.maked"
                    :todos="todo"
                    :choosed="choosed"
                    @del="todoList.splice(index,1)"
                    @choosed="chooseItem"
            ></check-box>
        </div>

        <h3>
            Выполнено
            <del-all-done-button :todos="todoList"></del-all-done-button>
        </h3>
        <div v-for="(todo, index) in todoList">
            <check-box
                    v-if="todo.maked"
                    :todos="todo"
                    :choosed="choosed"
                    @del="todoList.splice(index,1)"
                    @changed="choosed = -1"
            ></check-box>
        </div>
    </div>
</template>

<script>
    import NewItemForm from "./components/NewItemForm.vue"
    import CheckBox from "./components/CheckBox.vue"
    import DelAllDoneButton from "./components/DelAllDoneButton.vue"
    export default {
        components: {
            //hello,
            NewItemForm,
            CheckBox,
            DelAllDoneButton,
        },
        data() {
            return {
                todoList: [
                    {id: 1, maked: false, name: 'Milk'},
                    {id: 2, maked: false, name: 'second'},
                ],
                choosed: -1,
            }
        },
        methods:{
            chooseItem(choosedId) {
                this.choosed = choosedId;
            }
        },
    }
</script>