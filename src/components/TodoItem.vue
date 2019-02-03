<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
            <input type="checkbox" v-on:change="markComplete">
            {{ todo.title }}
            <button @click="$emit('del-todo', todo.id)" class="del">
                <i class="fa fa-trash" aria-hidden="true"></i>
            </button>
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
};
</script>

<style scoped>
.todo-item {
    background: #f4f4f4;
    padding: 15px;
    border-bottom: 1px #ccc dotted;
}

.is-complete {
    text-decoration: line-through;
}

.del {
    cursor: pointer;
    float: right;
}
</style>