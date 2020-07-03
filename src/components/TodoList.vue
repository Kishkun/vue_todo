<template>
    <div>
        <BaseInputText
                v-model="newTodoText"
                placeholder="New todo"
                @keydown.enter="addTodo"
        />
        <ul v-if="todos.length">
            <TodoListItem
                    v-for="todo in todos"
                    :key="todo.id"
                    :todo="todo"
                    @remove="removeTodo"
            />
        </ul>
    </div>
</template>
<script>
    import BaseInputText from "./BaseInputText";
    import TodoListItem from "./TodoListItem";

    let nextTodoId = 1;

    export default {
        name: "TodoList",
        data() {
            return {
                newTodoText: "",
                todos: [
                    {
                        id: nextTodoId++,
                        text: "CSS"
                    },
                    {
                        id: nextTodoId++,
                        text: "HTML"
                    },
                    {
                        id: nextTodoId++,
                        text: "JavaScript"
                    }
                ]
            }
        },
        methods: {
            addTodo() {
                let trimmedText = this.newTodoText.trim();
                if (trimmedText) {
                    this.todos.push({
                        id: nextTodoId++,
                        text: trimmedText
                    })
                    this.newTodoText = ""
                }
            },
            removeTodo (id) {
                this.todos = this.todos.filter(todo => {
                    return todo.id !== id
                })
            }
        },
        components: {
            BaseInputText,
            TodoListItem
        }
    }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
