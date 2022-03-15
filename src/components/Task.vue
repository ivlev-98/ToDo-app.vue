<template>
    <article class="task" :class="done ? 'done' : ''">
        <p>{{ text }}</p>
        <div class="task__buttons">
            <div class="task__btn success" @click="$emit('done', index)">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" width="1em" height="1em" fill="currentColor">
                    <path d="M438.6 105.4C451.1 117.9 451.1 138.1 438.6 150.6L182.6 406.6C170.1 419.1 149.9 419.1 137.4 406.6L9.372 278.6C-3.124 266.1-3.124 245.9 9.372 233.4C21.87 220.9 42.13 220.9 54.63 233.4L159.1 338.7L393.4 105.4C405.9 92.88 426.1 92.88 438.6 105.4H438.6z"/>
                </svg>
            </div>
            <div class="task__btn danger" @click="$emit('remove', index)">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" width="1em" height="1em" fill="currentColor">
                    <path d="M135.2 17.69C140.6 6.848 151.7 0 163.8 0H284.2C296.3 0 307.4 6.848 312.8 17.69L320 32H416C433.7 32 448 46.33 448 64C448 81.67 433.7 96 416 96H32C14.33 96 0 81.67 0 64C0 46.33 14.33 32 32 32H128L135.2 17.69zM394.8 466.1C393.2 492.3 372.3 512 346.9 512H101.1C75.75 512 54.77 492.3 53.19 466.1L31.1 128H416L394.8 466.1z"/>
                </svg>
            </div>
        </div>
    </article>
</template>

<script>
export default {
    name: 'Task',
    props: {
        text: String,
        done: Boolean,
        index: Number
    }
}
</script>

<style scoped>
.task {
    background: #f5f5f5;
    height: 45px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 15px;
    border-bottom: 1px solid #cad4da;
    transition: .5s;
}
.task.done {
    background: #73bd8b;
    color: #f5f5f5;
    text-decoration: line-through;
}
.task__buttons {
    display: flex;
    align-items: center;
    justify-content: center;
}
.task__btn {
    display: flex;
    width: 30px;
    height: 30px;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    margin: 0 5px;
    color: #f5f5f5;
    font-size: 12px;
    cursor: pointer;
    transition: .5s;
}
.task__btn.success {
    background: #2cb95b;
}
.task__btn.success:hover {
    background: #229448;
}
.task__btn.danger {
    background: #ca3030;
}
.task__btn.danger:hover {
    background: #ad2929;
}
</style>