<template>
    <div class="todo-item">
        <div class="item">
            <input type="checkbox" v-on:change="markComplete">
            <p v-bind:class="{'is-complete':todo.completed}">{{todo.title}}</p>
        </div>
        <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: lightgrey;
        padding: 10px;
        border-bottom: 1px grey dotted;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .item {
        display: flex;
        align-items: center;
        justify-content: start;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: lightseagreen;
        color: white;
        font-size: 1.2em;
        border: none;
        padding: 6px;
        cursor: pointer;
    }
</style>