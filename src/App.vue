<template>
    <header class="app-header">
        <h1>Simple ToDo App</h1>
    </header>
    <article class="error" v-if="error">
        <div>
            <p>{{ error }}</p>
            <button @click="error = ''">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" width="1em" height="1em" fill="currentColor">
                    <path d="M135.2 17.69C140.6 6.848 151.7 0 163.8 0H284.2C296.3 0 307.4 6.848 312.8 17.69L320 32H416C433.7 32 448 46.33 448 64C448 81.67 433.7 96 416 96H32C14.33 96 0 81.67 0 64C0 46.33 14.33 32 32 32H128L135.2 17.69zM394.8 466.1C393.2 492.3 372.3 512 346.9 512H101.1C75.75 512 54.77 492.3 53.19 466.1L31.1 128H416L394.8 466.1z"/>
                </svg>
            </button>
        </div>
    </article>
    <section class="tasks-list">
        <Task 
            v-for="(task, key) in todos"
            :text="task.text"
            :done="task.done"
            :index="key"
            :key="key"
            @remove="removeTask"
            @done="markDone" />
    </section>
    <form class="form">
        <input
            class="form__input"
            type="text"
            placeholder="Insert new task"
            v-model="newTodo"
            autofocus>
        <button class="form__btn" @click.prevent="addTask">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" width="1em" height="1em" fill="currentColor">
                <path d="M511.6 36.86l-64 415.1c-1.5 9.734-7.375 18.22-15.97 23.05c-4.844 2.719-10.27 4.097-15.68 4.097c-4.188 0-8.319-.8154-12.29-2.472l-122.6-51.1l-50.86 76.29C226.3 508.5 219.8 512 212.8 512C201.3 512 192 502.7 192 491.2v-96.18c0-7.115 2.372-14.03 6.742-19.64L416 96l-293.7 264.3L19.69 317.5C8.438 312.8 .8125 302.2 .0625 289.1s5.469-23.72 16.06-29.77l448-255.1c10.69-6.109 23.88-5.547 34 1.406S513.5 24.72 511.6 36.86z"/>
            </svg>
        </button>
    </form>
</template>

<script>
import Task from '@/components/Task.vue';

export default {
    name: 'App',
    components: {
        Task
    },
    data() {
        return {
            todos: [],
            newTodo: '',
            error: ''
        }
    },
    methods: {
        addTask() {
            if(this.newTodo.length > 3) {
                this.todos.unshift({text: this.newTodo, done: false});
                this.newTodo = '';
            }else
                this.error = 'The task cannot be shorter than 4 characters'
        },
        removeTask(index) {
            this.todos.splice(index, 1);
        },
        markDone(index) {
            this.todos[index].done = !this.todos[index].done;
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
@font-face {
    font-family: Helvetica;
    src: url('assets/fonts/Helvetica.ttf');
    font-display: swap;
}
body {
    font-family: Helvetica;
    background: #2391eb;
}
#app {
    width: 70%;
    margin: 30px auto;
    color: #718897;
    border-radius: 10px;
    overflow: hidden;
}
.app-header {
    background: #f5f5f5;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 55px;
    border-bottom: 1px solid #cad4da;
}
.app-header h1 {
    font-size: 1.5em;
}
.form {
    display: flex;
}
.form__input {
    display: block;
    width: 90%;
    height: 45px;
    border: none;
    padding: 0 15px;
}
.form__input:focus {
    outline: none;
}
.form__btn {
    width: 10%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #2391eb;
    background: #f5f5f5;
    border: none;
    font-size: 1.5em;
    cursor: pointer;
    transition: .5s;
}
.form__btn:hover {
    background: #cad4da;
}
.error {
    position: fixed;
    top: 40px;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}
.error div {
    background: #ca3030;
    color: #f5f5f5;
    padding: 20px 0 20px 15px;
    width: 50%;
    height: 45px;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    overflow: hidden;
}
.error button {
    height: 45px;
    width: 45px;
    background: #ca3030;
    color: #f5f5f5;
    border: none;
    transition: .5s;
}
.error button:hover {
    background: #a02626;
}
</style>
