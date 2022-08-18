<template>
    <MAT @close="changeModalAddTaskVisible" :mAT="modal_Add_Task" @addTodo="createTask"/>
    <div class="main__wrapper">
        <header class="header">
            <PrimaryButton @click="changeModalAddTaskVisible">
                <fa icon="circle-plus" class="add-task__icon" />Новая
                задача
            </PrimaryButton>
            <div class="pointer sun" @click="changeTheme()">
                <fa icon="sun" />
            </div>
            <div class="profile">
                <div>Здравствуйте, Анна!</div>
                <img src="@/assets/woman.png" alt="profile" class="profile__img" />
                <div class="profile__arrow pointer">
                    <fa icon="angle-down" />
                </div>
            </div>
        </header>
        <main class="main">
            <div class="column column-1">
                <Card>
                    <h3>Активные задачи</h3>
                    <TaskList :list="getActiveTodos(true)" @changeCompl="changeCompl" @deleter="removeTask"/>

                    <hr />

                    <h3>Завершенные задачи</h3>
                    <TaskList :list="getActiveTodos(false)" @changeCompl="changeCompl" />
                </Card>
                <Card />
            </div>
            <div class="column column-2">
                <Card />
            </div>
        </main>
    </div>
</template>

<script lang="js">
import PrimaryButton from "@/components/UI/PrimaryButton";
import Card from "@/components/UI/Card";
import TaskList from "@/components/TaskList";
import Modal_Add_Task from "@/components/Modal_Add_Task.vue"
export default {
    data() {
        return {
            todoList: [
                { id: 1, text: "Задача 1", completed: false },
                { id: 2, text: "Задача 2", completed: false },
                { id: 3, text: "Задача 3", completed: true },
            ],
            modal_Add_Task: false
        };
    },
    components: {
        PrimaryButton,
        Card,
        TaskList,
        MAT: Modal_Add_Task
    },
    methods: {
        changeTheme() {
            console.log("theme has been changed");
        },
        getActiveTodos(booly = true) {
            return this.todoList.filter(todo => todo.completed !== booly)
        },
        removeTask(id) {
            this.todoList = this.todoList.filter(todo => todo.id !== id)
        },
        changeCompl(id) {
            this.todoList.find(todo => todo.id === id).completed = !this.todoList.find(todo => todo.id === id).completed
        },
        changeModalAddTaskVisible(){
			this.modal_Add_Task = !this.modal_Add_Task
		},
        createTask (todo) {
            const newTodo = {
                id: new Date(),
                conpleted: false,
                text: todo.text
            }
            this.todoList.push(newTodo)
        }
    },
};
</script>

<style scoped>
.main__wrapper {
    position: fixed;
    width: calc(85% - 70px * 2);
    top: 0;
    right: 70px;
    bottom: 0;
}

.header {
    display: flex;
    margin: 10px 0 15px;
    justify-content: space-between;
    gap: 10px;
    align-items: center;
}

.sun {
    font-size: 1.5em;
    margin-right: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(153, 153, 153);
}

.sun:hover {
    color: rgb(171, 171, 171);
}

.add-task__icon {
    margin-right: 10px;
    font-size: 1.15em;
}

.main {
    display: flex;
    gap: 25px;
}

.profile {
    display: flex;
    align-items: center;
    gap: 20px;
}

.profile__img {
    width: 30px;
    height: 30px;
    border-radius: 50%;
}

.profile__arrow {
    background: #FAFAFA;
    box-shadow: 0px 10px 25px rgba(29, 52, 54, 0.08);
    border-radius: 5px;
    width: 24px;
    height: 24px;

    display: flex;
    justify-content: center;
    align-items: center;
}

.column {
    display: flex;
    flex-direction: column;
    gap: 30px;
}

.column-1 {
    flex: 0.9 1 auto;
}

.column-2 {
    flex: 1 1 auto;
}

hr {
    margin: 20px 0;
}
</style>