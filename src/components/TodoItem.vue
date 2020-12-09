<template>
<div class="todo-item" v-bind:class="{'is-completed':checked}">
    <p>
        <input type="checkbox" v-on:change="$emit('update-todo', todo.id)" @change="markComplete"/>
        {{todo.title}}
        <button class="del" @click="$emit('del-todo', todo.id)">x</button>
    </p>
</div>
</template>


<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    data() {
        return {
            checked: this.todo.completed
        }
    },
    methods: {
        markComplete() {
            this.checked = !this.checked;
            console.log(this.todo);
        }
    }
}
</script>

<style scoped>
.todo-item{
    background:#f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}

.is-completed{
    text-decoration: line-through;
}

.del{
    background: red;
    color: white;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}
</style>