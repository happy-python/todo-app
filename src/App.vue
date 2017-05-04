<template>
    <div>
        <h1 class="ui dividing centered header">Vue.js Todo App</h1>
        <TodoList :todos="todos"></TodoList>
        <CreateTodo @add-todo="addTodo"></CreateTodo>
    </div>
</template>

<script>
    import TodoList from './components/TodoList'
    import CreateTodo from './components/CreateTodo'

    export default {
        components: {
            TodoList,
            CreateTodo
        },
        methods:{
            addTodo(todo){
                this.todos.push(todo)
                swal("Success!", "To-Do created!", "success")
            }
        },
        data() {
            return {
                todos: [{
                    title: 'Todo A',
                    project: 'Project A',
                    done: false,
                }, {
                    title: 'Todo B',
                    project: 'Project B',
                    done: true,
                }, {
                    title: 'Todo C',
                    project: 'Project C',
                    done: false,
                }]
            }
        }
    }
</script>

<style>
    
</style>
