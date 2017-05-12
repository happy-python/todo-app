<template>
    <div>
    
        <!--JavaScript expressions in Vue are enclosed in double curly brackets.-->
    
        <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    
        <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    
        <!--we are now passing the data to the todo component to render the todo list-->
    
        <Todo v-for="(todo, index) in todos" :todo="todo" :key="index" @delete-todo="deleteTodo" @complete-todo="completeTodo"></Todo>
    </div>
</template>

<script>
import Todo from './Todo'

export default {
    props: ['todos'],
    components: {
        Todo
    },
    methods: {
        deleteTodo(todo) {
            swal({
                title: "Are you sure?",
                text: "This To-Do will be permanently deleted!",
                type: "warning",
                showCancelButton: true,
                confirmButtonColor: "#DD6B55",
                confirmButtonText: "Yes, delete it!",
                closeOnConfirm: false
            },
                () => {
                    const todoIndex = this.todos.indexOf(todo)
                    this.todos.splice(todoIndex, 1)
                    swal("Deleted!", "Your To-Do has been deleted.", "success")
                });
        },
        completeTodo(todo) {
            const todoIndex = this.todos.indexOf(todo)
            this.todos[todoIndex].done = true
            swal("Success!", "To-Do completed!", "success")
        }
    }
}
</script>

<style>
.tasks {
    text-align: center;
}
</style>