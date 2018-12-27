<template>
    <div>
        <new-item-form  @submit="NewTodo" />
        <h3>Не выполнено</h3>
        <div v-for="(todo, index) in todoList" :key="todo.id">
            <check-box v-if="!todo.maked" :todos="todo" :choosed="choosed" :index="index" @del="todoList.splice(index,1)"
                       @choosed="chooseItem" @changed="ChangeName" @canceled="Canceled"  />
        </div>
        <h3>
            Выполнено
            <input type="button" value="Удалить все" @click="DelAllDone"  />
        </h3>
        <div v-for="(todo, index) in todoList" :key="todo.id+'a'">
            <check-box v-if="todo.maked" :todos="todo" :choosed="choosed" :index="index" @del="todoList.splice(index,1)"
                       @choosed="chooseItem" @changed="ChangeName" @canceled="Canceled"  />
        </div>
    </div>
</template>

<script>
    import NewItemForm from "./components/NewItemForm.vue"
    import CheckBox from "./components/CheckBox.vue"

    export default {
        components: {
            NewItemForm,
            CheckBox,
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
            },
            // todo: имена с маленькой буквы
            ChangeName(newName) {
                this.todoList[newName[1]].name = newName[0];
                this.choosed = -1;
            },
            Canceled() {
                this.choosed = -1;
            },
            DelAllDone() {
                for ( let i=0; i<this.todoList.length; i++) {
                    if (this.todoList[i].maked) {
                        this.todoList.splice(i,1);
                        i--;
                    }
                }
            },
            NewTodo(newTodoName) {
                if (newTodoName) {
                    this.todoList.push({
                        id: (this.todoList[this.todoList.length-1].id+1),
                        maked: false,
                        name: newTodoName
                    });
                }
            }
        }
    }
</script>